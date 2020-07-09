---
title: Editor XML y diseñador de esquemas
ms.date: 11/04/2016
ms.topic: overview
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
ms.openlocfilehash: e763fa3475f26b9742ea5fb7061978e711eb22ea
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816428"
---
# <a name="overview-of-xml-tools-in-visual-studio"></a>Información general de las herramientas XML en Visual Studio

El *lenguaje de marcado extensible (XML)* es un lenguaje de marcado que proporciona un formato para describir datos. XML separa los datos y su presentación con hojas de estilos asociadas como Lenguaje de hojas de estilo extensible (XSL) y hojas de estilo CSS. Visual Studio incluye herramientas y características que facilitan el trabajo con XML, XSLT y esquemas XML.

## <a name="xml-editor"></a>Editor XML

El [Editor XML](xml-editor.md) se usa para editar documentos XML. Proporciona comprobación completa de sintaxis XML, validación de esquemas mientras se escribe, codificación en colores e IntelliSense. Cuando se proporciona un esquema o una definición de tipo de documento, IntelliSense lo utiliza para mostrar los elementos y atributos permitidos.

Otras características son:

- Compatibilidad con fragmentos XML, que incluye fragmentos generados por esquema.

- Esquematización de documentos, de manera que los elementos se pueden expandir y contraer.

- La capacidad de ejecutar transformaciones XSLT y ver los resultados en formato de texto, XML o HTML.

- La capacidad de generar esquemas de lenguaje de definición de esquemas XML (XSD) a partir del documento de instancia XML.

- Compatibilidad con la edición de hojas de estilos XSLT, que incluye compatibilidad con IntelliSense.

- Explorador de esquemas XML

## <a name="xml-schema-designer"></a>Diseñador de esquemas XML

El [Diseñador de esquemas XML](xml-schema-designer.md) está integrado en Visual Studio y en el Editor XML para permitirle trabajar con los esquemas del lenguaje de definición de esquemas XML (XSD).

## <a name="xslt-debugging"></a>Depuración de XSLT

Visual Studio permite la [depuración de hojas de estilos XSLT](../xml-tools/debugging-xslt.md). Mediante el depurador, puede definir puntos de interrupción en una hoja de estilos XSLT, ir a una hoja de estilos XSLT a partir del código, etc.

> [!NOTE]
> El depurador de XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="see-also"></a>Vea también

- <xref:System.Xml?displayProperty=fullName>
- [Transformaciones XSLT](/dotnet/standard/data/xml/xslt-transformations)
- [Procesamiento de datos XML con el modelo de datos XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)
- [Document Object Model (DOM) para XML](/dotnet/standard/data/xml/xml-document-object-model-dom)
- [Modelo de objetos de esquema XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)
