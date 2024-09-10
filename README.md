### Problema: Outboundfeeds muestra notas catalogadas como muro para sala plus

#### Pruebas 

> [!NOTE]
> El debugger en la UI no contiene la propiedad  `content_restrictions` en el ambiente de 
> **outboundfeeds-sandbox**, pero los otros ambientes sí la tienen.

* Añadi exclusión en el resolver
    * [Fuente: Setting up resolvers for Outbound Feeds](https://docs.arcxp.com/alc/en/how-to-set-up-resolvers-for-outbound-feeds?sys_kb_id=3ed9b99a47aa8610a87626c2846d43fc&id=kb_article_view&spa=1)
* Añadi en `Exclude-Terms` en la sección global de contenido la siguiente estructura: `[{"term": {"content_elements.content_code": "muro"}}]` (pruebas en el debugger de la UI)
    * [Fuente: How to Create a Custom Query with Outbound Feeds](https://docs.arcxp.com/alc/en/how-to-create-a-custom-query-with-outbound-feeds?sys_kb_id=e2202e4b47887990eee38788436d43cc&id=kb_article_view&spa=1)
* Cree un bloque personalizado para incluir un filtro
   ![Captura de pantalla 2024-09-10 104947](https://github.com/user-attachments/assets/ae6ded60-0624-478a-8445-68c19c3484d6)
    * [Fuente: Ejecting a Block with Outbound Feeds](https://docs.arcxp.com/alc/en/ejecting-a-block-with-outbound-feeds?sys_kb_id=6233a1d6c39f0e50a046930a05013158&id=kb_article_view&sysparm_rank=3&sysparm_tsqueryId=1d1cb13947e89a90a87626c2846d4396)
 
**El problema persistente: En ninguno de los casos probados funciona la exclusión de las notas de pago**


