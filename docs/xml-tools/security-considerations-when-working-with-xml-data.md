---
title: Consideraciones de seguridad al trabajar con datos XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f9d3c3e8ddffb72b04a9ca2fc0ec4df5eaac150
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62966710"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Consideraciones de seguridad al trabajar con datos XML

En este tema se describe los problemas de seguridad que debe conocer al trabajar con el editor XML o el depurador de XSLT.

## <a name="xml-editor"></a>Editor XML

 El editor XML se basa en el Editor de texto de Visual Studio. Depende de las clases <xref:System.Xml> y <xref:System.Xml.Xsl> para controlar muchos de los procesos XML.

- Las transformaciones XSLT se ejecutan en un nuevo dominio de aplicación. Las transformaciones XSLT son *en espacio aislado*; es decir, la directiva de seguridad de acceso de código de su equipo se utiliza para determinar los permisos restringidos según donde se encuentra la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

- La clase <xref:System.Xml.Xsl.XslCompiledTransform> se utiliza para compilar el XSLT al lenguaje intermedio de Microsoft con el fin de acelerar el rendimiento durante la ejecución.

- Los esquemas que apuntan a una ubicación externa en el archivo de catálogo se descargan automáticamente cuando el editor XML se carga por primera vez. La clase <xref:System.Xml.Schema.XmlSchemaSet> se utiliza para compilar los esquemas. El archivo de catálogo que se suministra con el editor XML no tienen vínculos a esquemas externos. El usuario tiene que agregar explícitamente una referencia al esquema externo antes de que el editor XML descargue el archivo de esquema. Descarga de HTTP puede deshabilitarse a través de la **otras opciones de herramientas** página para el editor XML.

- El editor XML utiliza el <xref:System.Net> clases para descargar esquemas

## <a name="xslt-debugger"></a>depurador de XSLT

 El depurador de XSLT utiliza el motor de depuración administrado de Visual Studio y las clases del espacio de nombres <xref:System.Xml> y <xref:System.Xml.Xsl>.

- El depurador ejecuta las transformaciones XSLT en un dominio de aplicación sandboxed. Se utiliza la directiva de seguridad de acceso del código del equipo para determinar los permisos restringidos según donde esté ubicada la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.

- La hoja de estilos XSLT se compila mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>.

- El evaluador de expresiones XSLT se carga mediante el motor de depuración administrado. Este motor asume que todo el código se ejecuta desde el equipo local del usuario. En consecuencia, la clase <xref:System.Xml.Xsl.XslCompiledTransform> descarga el archivo XSLT en el equipo local del usuario. La posibilidad de que ocurra un aumento en los privilegios de ejecución se mitiga con la ejecución de todas las transformaciones XSLT en un nuevo dominio de aplicación con permisos restringidos

## <a name="see-also"></a>Vea también

- [Dominios de aplicación](/dotnet/framework/app-domains/application-domains)