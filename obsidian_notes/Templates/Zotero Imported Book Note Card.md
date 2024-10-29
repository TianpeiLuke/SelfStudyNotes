---
tags:
  - book
aliases:
  - "{{citekey}}"
year: {{date | format ("YYYY")}} 
name: "{{title}}"
authors: "{{authors}}"
publication: "{{publicationTitle}}"
type: "{{itemType}}"
DOI: "{{DOI}}"
date of note: {{importDate | format("YYYY-MM-DD")}} 
---

> [!Cite]  
> {{bibliography}}

>[!Synth]  
>**Contribution**::  
>  
>**Related**:: {% for relation in relations | selectattr("citekey") %} [[@{{relation.citekey}}]]{% if not loop.last %}, {% endif%} {% endfor %}  
>  
  
>[!md]  
{% for type, creators in creators | groupby("creatorType") -%}  
{%- for creator in creators -%}  
> **{{"First" if loop.first}}{{type | capitalize}}**::  
{%- if creator.name %} {{creator.name}}  
{%- else %} {{creator.lastName}}, {{creator.firstName}}  
{%- endif %}  
{% endfor %}~  
{%- endfor %}  
> **Title**:: {{title}}  
> **Year**:: {{date | format("YYYY")}}  
> **Citekey**:: {{citekey}} {%- if itemType %}  
> **itemType**:: {{itemType}}{%- endif %}{%- if itemType == "journalArticle" %}  
> **Journal**:: *{{publicationTitle}}* {%- endif %}{%- if volume %}  
> **Volume**:: {{volume}} {%- endif %}{%- if issue %}  
> **Issue**:: {{issue}} {%- endif %}{%- if itemType == "bookSection" %}  
> **Book**:: {{publicationTitle}} {%- endif %}{%- if publisher %}  
> **Publisher**:: {{publisher}} {%- endif %}{%- if place %}  
> **Location**:: {{place}} {%- endif %}{%- if pages %}  
> **Pages**:: {{pages}} {%- endif %}{%- if DOI %}  
> **DOI**:: {{DOI}} {%- endif %}{%- if ISBN %}  
> **ISBN**:: {{ISBN}} {%- endif %}  


{%- for attachment in attachments | filterby("path", "endswith", ".pdf") %}  

> [!LINK]  
> 
> [{{attachment.title}}](file://{{attachment.path | replace(" ", "%20")}}) 
> 

{%- endfor -%}  



{%- if abstractNote %}  

> [!Abstract]  
> {{abstractNote}}  
> 

{%- endif -%} 









-----
## Reference
  
