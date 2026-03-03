 Gemini said

Aquí tienes toda nuestra conversación organizada en formato Markdown. Puedes copiar este contenido y guardarlo en un archivo con extensión .md (por ejemplo, bitacora_documentos.md).
Bitácora: Búsqueda de Herramientas para Generación de Documentos Self-Hosted
1. Consulta Inicial

Usuario: Busco una herramienta self-hosted para invoicing, propuestas de valor, brochures, etc., que permita cambiar el contenido fácilmente manteniendo estilos profesionales.

Respuesta: Se sugirieron tres opciones principales:

    Invoice Ninja: Sólido para facturas y propuestas, permite HTML/CSS personalizado.

    Odoo Community: ERP completo con motor de reportes QWeb.

    Crater: Opción moderna, ligera y minimalista para facturación.

2. Implementación en Invoice Ninja

Usuario: Instalé Invoice Ninja, ¿dónde agrego las plantillas HTML?

Respuesta: * Para facturas: Settings > Invoice Design > Custom Design.

    Para propuestas: Proposals > Templates (Requiere versión Pro).

    Tip: Usar variables como $client.name para automatizar el llenado.

3. Limitaciones de Versión y Alternativas

Usuario: No veo el menú de propuestas y busco algo que no se limite solo a facturas (brochures, etc.) sin depender de versiones Pro.

Respuesta: * Se explicó que "Proposals" es una función Pro/Enterprise en Invoice Ninja.

    Nuevas sugerencias:

        ERPNext: Totalmente Open Source, usa Jinja2/HTML para "Print Formats".

        Stack Custom: Baserow (datos) + n8n (automatización) + Gotenberg/Stirling-PDF (renderizado).

4. En busca de un motor de renderizado profesional

Usuario: Gotenberg no exporta correctamente. Busco un framework o librería moderna (estilo Ghostscript pero fácil) que usen las empresas para documentos profesionales.

Respuesta: Se identificaron tres estándares modernos:

    Carbone.io: Usa archivos de Word (.docx) como plantillas. Es ultra rápido y fiel al diseño original.

    WeasyPrint: Motor de renderizado enfocado en "CSS para impresión" (mejor que Chromium para PDFs).

    Typst: El sucesor moderno de LaTeX; rápido y con tipografía perfecta.

5. Depuración de Carbone.io

Usuario: Error al levantar Carbone con Docker: pull access denied for carbone-ee.

Respuesta: * Causa: El archivo docker-compose.yml intentaba bajar la versión Enterprise (ee) que requiere licencia.

    Solución: Cambiar a la versión Community.

    Configuración sugerida:
    YAML

    services:
      carbone-api:
        image: frozentech/carbone-api-community
        ports:
          - "4000:4000"
        volumes:
          - ./template:/app/template
          - ./render:/app/render

Resumen Técnico de Recomendación Final

Para el caso de uso de "Documento empresarial listo en segundos":

    Plantilla: Diseñada en Microsoft Word (fácil edición de estilos).

    Motor: Carbone Community Edition (Self-hosted via Docker).

    Flujo: Enviar JSON con datos a la API -> Recibir PDF perfecto.

¿Te gustaría que te prepare un script de ejemplo en Python o Node.js para enviar tus primeros datos a la API de Carbone una vez que la tengas corriendo?