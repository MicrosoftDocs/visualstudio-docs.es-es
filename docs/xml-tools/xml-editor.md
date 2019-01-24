---
title: Editor XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c5c1c81abbbc2f252744c465adf1cb99b3396d54
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873776"
---
# <a name="xml-editor"></a>Editor XML

El editor XML se basa en el editor de texto de Visual Studio e incluye compatibilidad adicional para los lenguajes XML. El editor XML incluye las siguientes características:

- Comprobación de sintaxis XML 1.0.

- Validación de esquemas mientras se escribe.

- Compatibilidad con fragmentos XML, que incluye fragmentos generados por esquema.

- Compatibilidad con Definición de tipo de documento (DTD).

- Compatibilidad con esquema de lenguaje de definición de esquemas XML (XSD).

- Creación de un esquema XML a partir de un documento de instancia XML.

- Conversión de una DTD o de un esquema reducido de datos XML (XDR) en un esquema XML.

- Comprobación de sintaxis XSLT 1.0.

- Esquematización de documentos, de manera que los elementos se pueden expandir y contraer.

- Integración con el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Esto proporciona una vista jerárquica de esquemas XML.

El editor XML se invoca para las extensiones de archivo conocidas, como *.xml*, *.xsd*, *.xsl*, y *.config*. También se invoca en extensión de archivo desconocidas si el archivo parece contener XML. También puede abrir cualquier archivo con el editor XML mediante el **abrir con** opción y seleccione el editor XML en la lista.

## <a name="xslt-intellisense"></a>XSLT IntelliSense

[XSLT IntelliSense](../xml-tools/xml-editor-intellisense-features.md) permite nombres de conjunto de atributos de Autocompletar, modos de plantilla y los nombres y nombres de parámetro para un modo o una especificada denominada plantilla.

## <a name="xslt-profiler"></a>Generador de perfiles XSLT

El [generador de perfiles XSLT](../xml-tools/walkthrough-xslt-profiler.md) crea rendimiento XSLT detallados informes que le ayudan a medir, evaluarán y solucionar problemas relacionados con el rendimiento en el código XSLT. El generador de perfiles XSLT incluye también sugerencias útiles para la optimización de hoja de estilos XSL y XSLT.

## <a name="xslt-hierarchy"></a>Jerarquía XSLT

El [herramienta de la jerarquía XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md) le permite agregar puntos de interrupción en las hojas de estilos incluidas y reglas de plantilla integradas.

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md) proporciona información sobre el editor de texto.
- [Referencia de las normas XML](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) proporciona información sobre las tecnologías XML, incluidos XML, definición de tipo de documento (DTD), lenguaje de definición de esquemas XML (XSD) y XSLT.
- [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)