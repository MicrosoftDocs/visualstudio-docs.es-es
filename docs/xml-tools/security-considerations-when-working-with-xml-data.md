---
title: Consideraciones de seguridad al trabajar con datos XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6db64424e1b503f4835f268fad9fdc5b8648b150
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572610"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Consideraciones de seguridad al trabajar con datos XML

En este tema se describen los aspectos de seguridad que debe conocer al trabajar con el Editor XML o el depurador de XSLT.

## <a name="xml-editor"></a>Editor XML

 El Editor XML se basa en el Editor de texto de Visual Studio. Depende de las clases <xref:System.Xml> y <xref:System.Xml.Xsl> para controlar muchos de los procesos XML.

-   Las transformaciones XSLT se ejecutan en un nuevo dominio de aplicación. Estas transformaciones son *en espacio aislado*; es decir, se utiliza la directiva de seguridad de acceso de código del equipo para determinar los permisos restringidos según donde esté ubicada la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

-   La clase <xref:System.Xml.Xsl.XslCompiledTransform> se utiliza para compilar el XSLT al lenguaje intermedio de Microsoft con el fin de acelerar el rendimiento durante la ejecución.

-   Los esquemas que apuntan a una ubicación externa del archivo de catálogo se descargan automáticamente cuando se carga primero el Editor XML. La clase <xref:System.Xml.Schema.XmlSchemaSet> se utiliza para compilar los esquemas. El archivo de catálogo que se suministra con el Editor XML no dispone de vínculos a esquemas externos. El usuario tiene que agregar explícitamente una referencia a un esquema externo antes de que el Editor XML descargue el archivo de esquema. Descarga HTTP se puede deshabilitar mediante la **opciones de herramientas varias** página del Editor XML.

-   El Editor XML utiliza las clases <xref:System.Net> para descargar esquemas

## <a name="xslt-debugger"></a>depurador de XSLT

 El depurador de XSLT utiliza el motor de depuración administrado de Visual Studio y las clases del espacio de nombres <xref:System.Xml> y <xref:System.Xml.Xsl>.

-   El depurador ejecuta las transformaciones XSLT en un dominio de aplicación sandboxed. Se utiliza la directiva de seguridad de acceso del código del equipo para determinar los permisos restringidos según donde esté ubicada la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

-   La hoja de estilos XSLT se compila mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>.

-   El evaluador de expresiones XSLT se carga mediante el motor de depuración administrado. Este motor asume que todo el código se ejecuta desde el equipo local del usuario. En consecuencia, la clase <xref:System.Xml.Xsl.XslCompiledTransform> descarga el archivo XSLT en el equipo local del usuario. La posibilidad de que ocurra un aumento en los privilegios de ejecución se mitiga con la ejecución de todas las transformaciones XSLT en un nuevo dominio de aplicación con permisos restringidos

## <a name="see-also"></a>Vea también

- [Dominios de aplicación](/dotnet/framework/app-domains/application-domains)