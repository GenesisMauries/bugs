### Problema: Outboundfeeds muestra notas catalogadas como muro (sala plus)

#### Pruebas 

> [!NOTE]
> En el entorno **outboundfeeds-sandbox**, el debugger (UI) no incluye la propiedad `content_restrictions`, mientras que en los otros entornos, sí está presente.
> 
* Añadi exclusión en el resolver
    * [Fuente: Setting up resolvers for Outbound Feeds](https://docs.arcxp.com/alc/en/how-to-set-up-resolvers-for-outbound-feeds?sys_kb_id=3ed9b99a47aa8610a87626c2846d43fc&id=kb_article_view&spa=1)
* Añadi en `Exclude-Terms` en la sección global de contenido las siguientes estructuras: `[{"term": {"content_elements.content_code": "muro"}}]` `[{"term": {"content_restrictions.content_code": "muro"}}]` (pruebas en el debugger de la UI)
    * [Fuente: How to Create a Custom Query with Outbound Feeds](https://docs.arcxp.com/alc/en/how-to-create-a-custom-query-with-outbound-feeds?sys_kb_id=e2202e4b47887990eee38788436d43cc&id=kb_article_view&spa=1)
* Cree un bloque personalizado para incluir un filtro
   ![Captura de pantalla 2024-09-10 104947](https://github.com/user-attachments/assets/ae6ded60-0624-478a-8445-68c19c3484d6)
    * [Fuente: Ejecting a Block with Outbound Feeds](https://docs.arcxp.com/alc/en/ejecting-a-block-with-outbound-feeds?sys_kb_id=6233a1d6c39f0e50a046930a05013158&id=kb_article_view&sysparm_rank=3&sysparm_tsqueryId=1d1cb13947e89a90a87626c2846d4396)

 * Añadi `"feedDefaultQuery": "[{\"bool\":{\"must_not\":[{\"term\":{\"content_restrictions.content_code\":\"muro\"}}],\"must\":[{\"term\":{\"type\":\"story\"}},{\"range\":{\"display_date\":{\"gte\":\"now-2d\",\"lte\":\"now\"}}}]}}]"` en `blocks.json`
      * [Fuente: Updating blocks.json and Outbound Feeds Development](https://arcxp.service-now.com/alc/en/updating-blocks-json-and-outbound-feeds-development?sys_kb_id=bfc85a99c34b4610a046930a05013108&id=kb_article_view&sysparm_rank=1&sysparm_tsqueryId=4cec970ac3a05a10a046930a0501311b)
      * [Fuente: Content Source Blocks in Outbound Feeds](https://arcxp.service-now.com/alc/en/content-source-blocks-in-outbound-feeds?sys_kb_id=df3733e6478cf590eee38788436d4314&id=kb_article_view&sysparm_rank=4&sysparm_tsqueryId=480bdb06c3a05a10a046930a050131db)


   
**El problema persistente: En ninguno de los casos probados funciona la exclusión de las notas de pago**

#### Preguntas

- ¿Existen otras configuraciones que debería probar para excluir correctamente el contenido?
- ¿Hay pasos adicionales que validar en las pruebas que realice?
- ¿Podrían proporcionar ejemplos de cómo han configurado con éxito exclusiones usando 'Exclude-Terms' o similares?
- ¿En donde exactamente podria filtrar la data? Si es en el codigo ¿en que parte/archivo especificamente? en la UI ¿donde?


