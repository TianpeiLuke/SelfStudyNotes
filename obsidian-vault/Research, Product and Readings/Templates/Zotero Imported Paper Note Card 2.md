---
tags:
- '#paper'
aliases: "{{citekey}}"
year: {{date | format ("YYYY")}}
name: "{{title}}"
authors: "{{authors}}"
publication: "{{publicationTitle}}"
type: "{{itemType}}"
DOI: "{{DOI}}"
date of note:
---

## {{title}} 
> [!info] 
> - **Abstract:** {{abstractNote}} 
> - **Sources**: [online]({{uri}}) [local]({{desktopURI}}) {%- for attachment in attachments | filterby("path", "endswith",".pdf") %} [pdf](file:///{{attachment.path | replace(" ","%20")}}) {% if loop.last %}{% endif %}{%- endfor %}
> - **Bibliography**: {{bibliography}}
> - **Cite Key:** [[@{{citekey}}]] 
 {%- if hashTags %}
> - **Tags:** {{hashTags}} 
{%- endif %}

>[!Personal Summary] 

## Annotations 
{% for annotation in annotations -%}{%- if annotation.annotatedText -%}{% if 'Purple' in annotation.colorCategory %} 
##### {{annotation.annotatedText | escape }}{% else %} 
<mark class="customZot-{% if annotation.color %}{{annotation.colorCategory}} {% endif %}">{{annotation.annotatedText | escape }}</mark> ([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}))
{% endif %}{%- endif %} {% if annotation.imageRelativePath %} ![[{{annotation.imageRelativePath}}]] {% endif %}{% if annotation.comment %}
>*{{annotation.comment}}* 
{% endif %}{% endfor -%}