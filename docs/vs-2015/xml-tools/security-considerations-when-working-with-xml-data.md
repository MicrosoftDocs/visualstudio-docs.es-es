---
title: Consideraciones de seguridad al trabajar con datos XML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87f1fad820cbc7387779862c0c010b01cab0303e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302476"
---
# <a name="security-considerations-when-working-with-xml-data"></a>Consideraciones de seguridad al trabajar con datos XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
En este tema se describen los aspectos de seguridad que debe conocer al trabajar con el Editor XML o el depurador de XSLT.  
  
## <a name="xml-editor"></a>Editor XML  
 El Editor XML se basa en el Editor de texto de Visual Studio. Depende de las clases <xref:System.Xml> y <xref:System.Xml.Xsl> para controlar muchos de los procesos XML.  
  
-   Las transformaciones XSLT se ejecutan en un nuevo dominio de aplicación. Las transformaciones XSLT son *en espacio aislado*; es decir, la directiva de seguridad de acceso de código de su equipo se utiliza para determinar los permisos restringidos según donde se encuentra la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.  
  
-   La clase <xref:System.Xml.Xsl.XslCompiledTransform> se utiliza para compilar el XSLT al lenguaje intermedio de Microsoft con el fin de acelerar el rendimiento durante la ejecución.  
  
-   Los esquemas que apuntan a una ubicación externa del archivo de catálogo se descargan automáticamente cuando se carga primero el Editor XML. La clase <xref:System.Xml.Schema.XmlSchemaSet> se utiliza para compilar los esquemas. El archivo de catálogo que se suministra con el Editor XML no dispone de vínculos a esquemas externos. El usuario tiene que agregar explícitamente una referencia a un esquema externo antes de que el Editor XML descargue el archivo de esquema. Descarga de HTTP puede deshabilitarse a través de la **otras opciones de herramientas** página del Editor XML.  
  
-   El Editor XML utiliza las clases <xref:System.Net> para descargar esquemas  
  
## <a name="xslt-debugger"></a>Depurador de XSLT  
 El depurador de XSLT utiliza el motor de depuración administrado de Visual Studio y las clases del espacio de nombres <xref:System.Xml> y <xref:System.Xml.Xsl>.  
  
-   El depurador ejecuta las transformaciones XSLT en un dominio de aplicación sandboxed. Se utiliza la directiva de seguridad de acceso del código del equipo para determinar los permisos restringidos según donde esté ubicada la hoja de estilos XSLT. Por ejemplo, las hojas de estilos de una ubicación de Internet tienen los permisos más restringidos, mientras que las hojas de estilos que se copian en el disco duro se ejecutan con plena confianza.  
  
-   La hoja de estilos XSLT se compila mediante la clase <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   El evaluador de expresiones XSLT se carga mediante el motor de depuración administrado. Este motor asume que todo el código se ejecuta desde el equipo local del usuario. En consecuencia, la clase <xref:System.Xml.Xsl.XslCompiledTransform> descarga el archivo XSLT en el equipo local del usuario. La posibilidad de que ocurra un aumento en los privilegios de ejecución se mitiga con la ejecución de todas las transformaciones XSLT en un nuevo dominio de aplicación con permisos restringidos  
  
## <a name="see-also"></a>Vea también  
 [Dominios de aplicación](http://msdn.microsoft.com/en-us/39e57d07-a740-4cd4-ae82-e119ea3856c1)



