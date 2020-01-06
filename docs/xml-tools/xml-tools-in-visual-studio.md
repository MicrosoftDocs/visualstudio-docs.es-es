---
title: Editor XML y diseñador de esquemas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87a5f069d5255a744e256bc9f7d1b48a135e85d8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592313"
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio

*Extensible Markup Language (XML)* es un lenguaje de marcado que proporciona un formato para describir los datos. XML separa los datos y su presentación usando hojas de estilos asociadas como Extensible Stylesheet Language (XSL) y hojas de estilos en cascada (CSS). Visual Studio incluye herramientas y características que facilitan el trabajo con XML, XSLT y esquemas XML.

## <a name="xml-editor"></a>Editor XML

El [Editor XML](xml-editor.md) se utiliza para editar documentos XML. Proporciona una comprobación completa de la sintaxis XML, la validación del esquema mientras escribe, codificación de colores e IntelliSense. Cuando se proporciona un esquema o una definición de tipo de documento, IntelliSense lo utiliza para mostrar los elementos y atributos permitidos.

Otras características son:

- Compatibilidad con fragmentos XML, incluidos fragmentos de código generados por esquema

- Esquematización de documentos para que los elementos puedan expandirse y contraerse

- La capacidad de ejecutar transformaciones XSLT y ver los resultados como texto, XML o HTML.

- La capacidad de generar esquemas del lenguaje de definición de esquemas XML (XSD) a partir del documento de instancia XML

- Compatibilidad con la edición de hojas de estilos XSLT, incluida la compatibilidad con IntelliSense

- Explorador de esquemas XML

## <a name="xml-schema-designer"></a>Diseñador de esquemas XML

El [Diseñador de esquemas XML](xml-schema-designer.md) se integra con Visual Studio y el editor XML para que pueda trabajar con esquemas del lenguaje de definición de esquemas XML (XSD).

## <a name="xslt-debugging"></a>Depuración de XSLT

Visual Studio admite la [depuración de hojas de estilos XSLT](../xml-tools/debugging-xslt.md). Mediante el depurador, puede definir puntos de interrupción en una hoja de estilos XSLT, ir a una hoja de estilos XSLT a partir del código, etc.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="see-also"></a>Vea también

- <xref:System.Xml?displayProperty=fullName>
- [Transformaciones XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Procesar datos XML mediante el modelo de datos de XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Document Object Model (DOM) para XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Modelo de objetos de esquema XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)
