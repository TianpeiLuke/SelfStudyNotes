---
tags:
  - design
  - mcp
  - server_architecture
  - agent_specifications
  - tool_definitions
keywords:
  - MCP servers
  - tool specifications
  - resource definitions
  - agent architecture
  - server configuration
topics:
  - MCP server specifications
  - agent tool definitions
  - resource management
  - server configuration
language: python
date of note: 2025-08-09
---

# MCP Agentic Workflow Server Architecture Design

## Overview

This document defines the detailed specifications for all MCP servers in the agentic workflow system. Each server provides specialized tools and resources for specific aspects of the pipeline development workflow.

## Related Documents

### Master Design
- [MCP Agentic Workflow Master Design](mcp_agentic_workflow_master_design.md) - Complete system overview

### Related Components
- [MCP Workflow Implementation Design](mcp_agentic_workflow_implementation.md) - Workflow sequences and phases
- [MCP Agent Integration Design](mcp_agentic_workflow_agent_integration.md) - Agent coordination patterns
- [MCP Validation Framework Design](mcp_agentic_workflow_validation_framework.md) - Validation system details

## MCP Server Specifications

### 1. Workflow Orchestrator MCP Server

**Server Name**: `agentic-workflow-orchestrator`
**Purpose**: Central workflow coordination and state management
**Port**: 8001

#### Server Configuration
```json
{
  "name": "agentic-workflow-orchestrator",
  "version": "1.0.0",
  "description": "Central workflow coordination and state management",
  "capabilities": {
    "workflow_management": true,
    "state_persistence": true,
    "human_interaction": true,
    "convergence_evaluation": true
  }
}
```

#### Tools
```json
{
  "start_workflow": {
    "description": "Initialize new agentic workflow instance",
    "inputSchema": {
      "type": "object",
      "properties": {
        "user_requirements": {"type": "string"},
        "step_type": {"type": "string", "enum": ["Processing", "Training", "Transform", "CreateModel"]},
        "documentation_location": {"type": "string"},
        "workflow_id": {"type": "string"}
      },
      "required": ["user_requirements", "step_type", "documentation_location"]
    }
  },
  "transition_workflow_state": {
    "description": "Move workflow to next phase",
    "inputSchema": {
      "type": "object",
      "properties": {
        "workflow_id": {"type": "string"},
        "current_phase": {"type": "string"},
        "next_phase": {"type": "string"},
        "transition_data": {"type": "object"}
      },
      "required": ["workflow_id", "current_phase", "next_phase"]
    }
  },
  "check_convergence_criteria": {
    "description": "Evaluate if workflow phase has converged",
    "inputSchema": {
      "type": "object",
      "properties": {
        "workflow_id": {"type": "string"},
        "phase": {"type": "string"},
        "validation_results": {"type": "object"},
        "iteration_count": {"type": "integer"}
      },
      "required": ["workflow_id", "phase", "validation_results"]
    }
  },
  "manage_human_interaction": {
    "description": "Handle human-in-the-loop interactions",
    "inputSchema": {
      "type": "object",
      "properties": {
        "workflow_id": {"type": "string"},
        "interaction_type": {"type": "string", "enum": ["approval", "feedback", "clarification"]},
        "context": {"type": "object"},
        "timeout_seconds": {"type": "integer", "default": 3600}
      },
      "required": ["workflow_id", "interaction_type", "context"]
    }
  },
  "get_workflow_status": {
    "description": "Get current workflow status and progress",
    "inputSchema": {
      "type": "object",
      "properties": {
        "workflow_id": {"type": "string"}
      },
      "required": ["workflow_id"]
    }
  }
}
```

#### Resources
```json
{
  "workflow_templates": {
    "uri": "workflow://templates/",
    "description": "Workflow phase templates and configurations"
  },
  "convergence_criteria": {
    "uri": "workflow://criteria/",
    "description": "Convergence criteria definitions for each phase"
  },
  "human_interaction_templates": {
    "uri": "workflow://human/",
    "description": "Templates for human interaction interfaces"
  }
}
```

### 2. Planner Agent MCP Server

**Server Name**: `pipeline-planner-agent`
**Purpose**: Implementation planning and plan revision
**Port**: 8002

#### Server Configuration
```json
{
  "name": "pipeline-planner-agent",
  "version": "1.0.0",
  "description": "Implementation planning and plan revision",
  "capabilities": {
    "plan_generation": true,
    "requirements_analysis": true,
    "pattern_selection": true,
    "plan_revision": true
  }
}
```

#### Tools
```json
{
  "create_implementation_plan": {
    "description": "Generate initial implementation plan for pipeline step",
    "inputSchema": {
      "type": "object",
      "properties": {
        "requirements": {"type": "string"},
        "step_type": {"type": "string"},
        "design_patterns": {"type": "array", "items": {"type": "string"}},
        "documentation_location": {"type": "string"},
        "workflow_context": {"type": "object"}
      },
      "required": ["requirements", "step_type", "documentation_location"]
    }
  },
  "revise_implementation_plan": {
    "description": "Revise plan based on validation feedback",
    "inputSchema": {
      "type": "object",
      "properties": {
        "original_plan": {"type": "object"},
        "validation_feedback": {"type": "object"},
        "revision_iteration": {"type": "integer"},
        "focus_areas": {"type": "array", "items": {"type": "string"}}
      },
      "required": ["original_plan", "validation_feedback"]
    }
  },
  "analyze_requirements": {
    "description": "Analyze user requirements and categorize step type",
    "inputSchema": {
      "type": "object",
      "properties": {
        "requirements_text": {"type": "string"},
        "context_information": {"type": "object"}
      },
      "required": ["requirements_text"]
    }
  },
  "select_design_patterns": {
    "description": "Select appropriate design patterns based on step type",
    "inputSchema": {
      "type": "object",
      "properties": {
        "step_type": {"type": "string"},
        "requirements": {"type": "string"},
        "existing_patterns": {"type": "array"}
      },
      "required": ["step_type", "requirements"]
    }
  }
}
```

#### Resources
```json
{
  "developer_guide": {
    "uri": "knowledge://developer_guide/",
    "description": "Complete developer guide documentation"
  },
  "design_patterns": {
    "uri": "knowledge://design_patterns/",
    "description": "Design pattern documents and examples"
  },
  "implementation_examples": {
    "uri": "knowledge://examples/",
    "description": "Existing implementation examples"
  },
  "planning_templates": {
    "uri": "templates://planning/",
    "description": "Plan generation templates and formats"
  }
}
```

### 3. Validator Agent MCP Server

**Server Name**: `pipeline-validator-agent`
**Purpose**: Two-level validation with LLM analysis and deterministic tools
**Port**: 8003

#### Server Configuration
```json
{
  "name": "pipeline-validator-agent",
  "version": "1.0.0",
  "description": "Two-level validation with LLM analysis and deterministic tools",
  "capabilities": {
    "llm_validation": true,
    "deterministic_validation": true,
    "architectural_analysis": true,
    "cross_component_validation": true
  }
}
```

#### Tools
```json
{
  "validate_plan_level1": {
    "description": "LLM-based plan validation (Level 1 only)",
    "inputSchema": {
      "type": "object",
      "properties": {
        "implementation_plan": {"type": "object"},
        "validation_rules": {"type": "array"},
        "architectural_context": {"type": "object"}
      },
      "required": ["implementation_plan"]
    }
  },
  "validate_code_level1": {
    "description": "LLM-based code validation",
    "inputSchema": {
      "type": "object",
      "properties": {
        "component_code": {"type": "object"},
        "architectural_patterns": {"type": "array"},
        "validation_scope": {"type": "string"}
      },
      "required": ["component_code"]
    }
  },
  "validate_code_level2": {
    "description": "Two-level validation with deterministic tools",
    "inputSchema": {
      "type": "object",
      "properties": {
        "component_paths": {"type": "object"},
        "validation_tools": {"type": "array"},
        "pattern_context": {"type": "object"},
        "strict_mode": {"type": "boolean", "default": true}
      },
      "required": ["component_paths"]
    }
  },
  "validate_script_contract_strict": {
    "description": "Strict validation of script-contract alignment",
    "inputSchema": {
      "type": "object",
      "properties": {
        "script_path": {"type": "string"},
        "contract_path": {"type": "string"},
        "pattern_context": {"type": "object"}
      },
      "required": ["script_path", "contract_path"]
    }
  },
  "validate_contract_spec_strict": {
    "description": "Strict validation of contract-specification alignment",
    "inputSchema": {
      "type": "object",
      "properties": {
        "contract_path": {"type": "string"},
        "spec_path": {"type": "string"},
        "pattern_context": {"type": "object"}
      },
      "required": ["contract_path", "spec_path"]
    }
  },
  "validate_spec_dependencies_strict": {
    "description": "Strict validation of specification dependencies",
    "inputSchema": {
      "type": "object",
      "properties": {
        "spec_path": {"type": "string"},
        "pipeline_context": {"type": "object"},
        "dependency_patterns": {"type": "array"}
      },
      "required": ["spec_path", "pipeline_context"]
    }
  },
  "validate_builder_config_strict": {
    "description": "Strict validation of builder-configuration alignment",
    "inputSchema": {
      "type": "object",
      "properties": {
        "builder_path": {"type": "string"},
        "config_path": {"type": "string"},
        "usage_patterns": {"type": "array"}
      },
      "required": ["builder_path", "config_path"]
    }
  },
  "analyze_architectural_patterns": {
    "description": "Identify architectural patterns in components",
    "inputSchema": {
      "type": "object",
      "properties": {
        "component_paths": {"type": "object"},
        "analysis_scope": {"type": "string", "enum": ["full_component_analysis", "targeted_analysis"]},
        "pattern_library": {"type": "array"}
      },
      "required": ["component_paths", "analysis_scope"]
    }
  },
  "check_cross_component_alignment": {
    "description": "Validate alignment across multiple components",
    "inputSchema": {
      "type": "object",
      "properties": {
        "component_set": {"type": "object"},
        "alignment_rules": {"type": "array"},
        "consistency_checks": {"type": "array"}
      },
      "required": ["component_set", "alignment_rules"]
    }
  }
}
```

#### Resources
```json
{
  "validation_framework": {
    "uri": "knowledge://validation/",
    "description": "Validation framework documentation and tools"
  },
  "alignment_rules": {
    "uri": "knowledge://alignment/",
    "description": "Alignment rules and validation checklists"
  },
  "validation_tools": {
    "uri": "tools://validation/",
    "description": "Deterministic validation tools and scripts"
  },
  "pattern_library": {
    "uri": "knowledge://patterns/",
    "description": "Architectural pattern library for validation"
  }
}
```

### 4. Programmer Agent MCP Server

**Server Name**: `pipeline-programmer-agent`
**Purpose**: Code generation and refinement based on validated plans
**Port**: 8004

#### Server Configuration
```json
{
  "name": "pipeline-programmer-agent",
  "version": "1.0.0",
  "description": "Code generation and refinement based on validated plans",
  "capabilities": {
    "code_generation": true,
    "component_creation": true,
    "code_refinement": true,
    "registry_management": true
  }
}
```

#### Tools
```json
{
  "generate_step_components": {
    "description": "Generate all step components from validated plan",
    "inputSchema": {
      "type": "object",
      "properties": {
        "implementation_plan": {"type": "object"},
        "step_type": {"type": "string"},
        "design_patterns": {"type": "array"},
        "generation_options": {"type": "object"}
      },
      "required": ["implementation_plan", "step_type"]
    }
  },
  "refine_code_implementation": {
    "description": "Refine code based on validation feedback",
    "inputSchema": {
      "type": "object",
      "properties": {
        "current_implementation": {"type": "object"},
        "validation_feedback": {"type": "object"},
        "refinement_focus": {"type": "array"},
        "preserve_patterns": {"type": "boolean", "default": true}
      },
      "required": ["current_implementation", "validation_feedback"]
    }
  },
  "create_script_contract": {
    "description": "Generate script contract component",
    "inputSchema": {
      "type": "object",
      "properties": {
        "contract_specification": {"type": "object"},
        "step_type": {"type": "string"},
        "template_options": {"type": "object"}
      },
      "required": ["contract_specification", "step_type"]
    }
  },
  "create_step_specification": {
    "description": "Generate step specification component",
    "inputSchema": {
      "type": "object",
      "properties": {
        "spec_requirements": {"type": "object"},
        "dependency_patterns": {"type": "array"},
        "output_patterns": {"type": "array"}
      },
      "required": ["spec_requirements"]
    }
  },
  "create_configuration_class": {
    "description": "Generate configuration class component",
    "inputSchema": {
      "type": "object",
      "properties": {
        "config_specification": {"type": "object"},
        "base_class": {"type": "string"},
        "three_tier_design": {"type": "boolean", "default": true}
      },
      "required": ["config_specification"]
    }
  },
  "create_step_builder": {
    "description": "Generate step builder component",
    "inputSchema": {
      "type": "object",
      "properties": {
        "builder_specification": {"type": "object"},
        "step_type": {"type": "string"},
        "integration_patterns": {"type": "array"}
      },
      "required": ["builder_specification", "step_type"]
    }
  },
  "create_processing_script": {
    "description": "Generate processing script component",
    "inputSchema": {
      "type": "object",
      "properties": {
        "script_specification": {"type": "object"},
        "business_logic": {"type": "string"},
        "error_handling_patterns": {"type": "array"}
      },
      "required": ["script_specification", "business_logic"]
    }
  },
  "update_registry_files": {
    "description": "Update registry and import files",
    "inputSchema": {
      "type": "object",
      "properties": {
        "step_name": {"type": "string"},
        "component_info": {"type": "object"},
        "registry_updates": {"type": "array"}
      },
      "required": ["step_name", "component_info"]
    }
  }
}
```

#### Resources
```json
{
  "implementation_examples": {
    "uri": "knowledge://examples/",
    "description": "Existing implementation examples and patterns"
  },
  "code_templates": {
    "uri": "templates://code/",
    "description": "Code generation templates and boilerplate"
  },
  "pattern_implementations": {
    "uri": "knowledge://implementations/",
    "description": "Pattern-specific implementation examples"
  },
  "registry_templates": {
    "uri": "templates://registry/",
    "description": "Registry update templates and patterns"
  }
}
```

### 5. Documentation Manager MCP Server

**Server Name**: `documentation-manager`
**Purpose**: Documentation creation, management, and version control
**Port**: 8005

#### Server Configuration
```json
{
  "name": "documentation-manager",
  "version": "1.0.0",
  "description": "Documentation creation, management, and version control",
  "capabilities": {
    "document_creation": true,
    "yaml_frontmatter": true,
    "version_control": true,
    "report_generation": true
  }
}
```

#### Tools
```json
{
  "create_plan_document": {
    "description": "Create implementation plan document with YAML frontmatter",
    "inputSchema": {
      "type": "object",
      "properties": {
        "plan_content": {"type": "object"},
        "document_location": {"type": "string"},
        "yaml_metadata": {"type": "object"},
        "version_info": {"type": "object"}
      },
      "required": ["plan_content", "document_location"]
    }
  },
  "create_validation_report": {
    "description": "Create validation report document",
    "inputSchema": {
      "type": "object",
      "properties": {
        "validation_results": {"type": "object"},
        "report_location": {"type": "string"},
        "report_type": {"type": "string", "enum": ["plan_validation", "code_validation"]},
        "metadata": {"type": "object"}
      },
      "required": ["validation_results", "report_location", "report_type"]
    }
  },
  "update_documentation": {
    "description": "Update existing documentation",
    "inputSchema": {
      "type": "object",
      "properties": {
        "document_path": {"type": "string"},
        "updates": {"type": "object"},
        "update_type": {"type": "string", "enum": ["append", "replace", "merge"]},
        "backup": {"type": "boolean", "default": true}
      },
      "required": ["document_path", "updates", "update_type"]
    }
  },
  "track_document_versions": {
    "description": "Version control for workflow documents",
    "inputSchema": {
      "type": "object",
      "properties": {
        "document_path": {"type": "string"},
        "version_action": {"type": "string", "enum": ["create", "update", "finalize"]},
        "version_metadata": {"type": "object"}
      },
      "required": ["document_path", "version_action"]
    }
  },
  "generate_yaml_frontmatter": {
    "description": "Generate YAML frontmatter for documents",
    "inputSchema": {
      "type": "object",
      "properties": {
        "document_type": {"type": "string"},
        "content_analysis": {"type": "object"},
        "custom_tags": {"type": "array"},
        "custom_keywords": {"type": "array"}
      },
      "required": ["document_type"]
    }
  }
}
```

#### Resources
```json
{
  "documentation_templates": {
    "uri": "templates://documentation/",
    "description": "Documentation templates and formats"
  },
  "yaml_standards": {
    "uri": "standards://yaml/",
    "description": "YAML frontmatter standards and examples"
  },
  "version_control": {
    "uri": "vcs://documents/",
    "description": "Document version control and history"
  }
}
```

### 6. Knowledge Base MCP Server

**Server Name**: `pipeline-knowledge-base`
**Purpose**: Centralized access to all knowledge resources
**Port**: 8006

#### Server Configuration
```json
{
  "name": "pipeline-knowledge-base",
  "version": "1.0.0",
  "description": "Centralized access to all knowledge resources",
  "capabilities": {
    "knowledge_access": true,
    "semantic_search": true,
    "resource_management": true,
    "content_indexing": true
  }
}
```

#### Resources
```json
{
  "developer_guide": {
    "uri": "file://slipbox/0_developer_guide/",
    "description": "Complete developer guide documentation",
    "mimeType": "text/markdown"
  },
  "design_patterns": {
    "uri": "file://slipbox/1_design/",
    "description": "Design pattern documents and architecture",
    "mimeType": "text/markdown"
  },
  "implementation_examples": {
    "uri": "file://src/cursus/steps/",
    "description": "Existing step implementations",
    "mimeType": "text/python"
  },
  "validation_tools": {
    "uri": "file://src/cursus/validation/",
    "description": "Validation tools and frameworks",
    "mimeType": "text/python"
  },
  "prompt_templates": {
    "uri": "file://slipbox/3_llm_developer/developer_prompt_templates/",
    "description": "Current prompt templates",
    "mimeType": "text/markdown"
  },
  "project_planning": {
    "uri": "file://slipbox/2_project_planning/",
    "description": "Project planning documents and history",
    "mimeType": "text/markdown"
  }
}
```

## Server Deployment Configuration

### Docker Compose Configuration
```yaml
version: '3.8'
services:
  workflow-orchestrator:
    image: mcp-workflow-orchestrator:latest
    ports:
      - "8001:8001"
    environment:
      - MCP_SERVER_NAME=agentic-workflow-orchestrator
      - MCP_SERVER_PORT=8001
    volumes:
      - ./data/workflows:/data/workflows
      - ./config/orchestrator:/config
    depends_on:
      - redis
      - postgres

  planner-agent:
    image: mcp-planner-agent:latest
    ports:
      - "8002:8002"
    environment:
      - MCP_SERVER_NAME=pipeline-planner-agent
      - MCP_SERVER_PORT=8002
      - KNOWLEDGE_BASE_URL=http://knowledge-base:8006
    volumes:
      - ./config/planner:/config

  validator-agent:
    image: mcp-validator-agent:latest
    ports:
      - "8003:8003"
    environment:
      - MCP_SERVER_NAME=pipeline-validator-agent
      - MCP_SERVER_PORT=8003
      - KNOWLEDGE_BASE_URL=http://knowledge-base:8006
    volumes:
      - ./config/validator:/config
      - ./validation-tools:/tools

  programmer-agent:
    image: mcp-programmer-agent:latest
    ports:
      - "8004:8004"
    environment:
      - MCP_SERVER_NAME=pipeline-programmer-agent
      - MCP_SERVER_PORT=8004
      - KNOWLEDGE_BASE_URL=http://knowledge-base:8006
    volumes:
      - ./config/programmer:/config
      - ./code-templates:/templates

  documentation-manager:
    image: mcp-documentation-manager:latest
    ports:
      - "8005:8005"
    environment:
      - MCP_SERVER_NAME=documentation-manager
      - MCP_SERVER_PORT=8005
    volumes:
      - ./config/documentation:/config
      - ./documents:/documents

  knowledge-base:
    image: mcp-knowledge-base:latest
    ports:
      - "8006:8006"
    environment:
      - MCP_SERVER_NAME=pipeline-knowledge-base
      - MCP_SERVER_PORT=8006
    volumes:
      - ./slipbox:/knowledge/slipbox
      - ./src:/knowledge/src
      - ./config/knowledge-base:/config

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis-data:/data

  postgres:
    image: postgres:15-alpine
    environment:
      - POSTGRES_DB=workflow_db
      - POSTGRES_USER=workflow_user
      - POSTGRES_PASSWORD=workflow_pass
    volumes:
      - postgres-data:/var/lib/postgresql/data

volumes:
  redis-data:
  postgres-data:
```

### Environment Configuration
```bash
# MCP Server Configuration
export MCP_ORCHESTRATOR_URL="http://localhost:8001"
export MCP_PLANNER_URL="http://localhost:8002"
export MCP_VALIDATOR_URL="http://localhost:8003"
export MCP_PROGRAMMER_URL="http://localhost:8004"
export MCP_DOCUMENTATION_URL="http://localhost:8005"
export MCP_KNOWLEDGE_BASE_URL="http://localhost:8006"

# Database Configuration
export REDIS_URL="redis://localhost:6379"
export POSTGRES_URL="postgresql://workflow_user:workflow_pass@localhost:5432/workflow_db"

# Security Configuration
export MCP_AUTH_TOKEN="your-secure-auth-token"
export MCP_ENCRYPTION_KEY="your-encryption-key"

# Performance Configuration
export MCP_CACHE_TTL=3600
export MCP_MAX_CONCURRENT_WORKFLOWS=10
export MCP_AGENT_TIMEOUT=300
```

## Server Health Monitoring

### Health Check Endpoints
Each MCP server provides standard health check endpoints:

```json
{
  "health_endpoints": {
    "liveness": "/health/live",
    "readiness": "/health/ready",
    "metrics": "/metrics",
    "status": "/status"
  }
}
```

### Monitoring Configuration
```yaml
monitoring:
  prometheus:
    enabled: true
    port: 9090
    scrape_interval: 30s
  
  grafana:
    enabled: true
    port: 3000
    dashboards:
      - workflow_overview
      - agent_performance
      - validation_metrics
  
  alerting:
    enabled: true
    rules:
      - agent_down
      - high_error_rate
      - slow_response_time
      - workflow_failure
```

## Conclusion

This server architecture design provides a comprehensive specification for all MCP servers in the agentic workflow system. Each server is designed with clear responsibilities, standardized interfaces, and robust configuration options.

The modular architecture enables independent development, deployment, and scaling of each component while maintaining consistent communication patterns and resource access. The detailed tool and resource specifications provide clear contracts for inter-agent communication and system integration.

The deployment configuration and monitoring setup ensure reliable operation in production environments with proper observability and maintenance capabilities.
