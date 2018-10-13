---
title: Validación de documentos XML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a09e4346c84982bdac6fa740c53dedf6444f9268
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211528"
---
# <a name="xml-document-validation"></a>Validación de documentos XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML comprueba la sintaxis XML 1.0 y realiza la validación de los datos mientras escribe. Para realizar la validación, el editor utiliza una definición de tipo de documento (DTD) o un esquema. Un subrayado ondulado rojo resalta los errores de XML 1.0 con un formato correcto. Un subrayado ondulado azul muestra errores semánticos basados en la validación de DTD o de esquemas. Cada error posee una entrada asociada en la lista de errores. También puede ver el mensaje de error si detiene el mouse sobre el subrayado ondulado.  
  
 Para encontrar los esquemas usados en la validación se hace coincidir el `targetNamespace` de un esquema compilado con la declaración xmlns del elemento. Los esquemas compilados se cargan desde una de las siguientes ubicaciones, mostradas en orden de prioridad:  
  
-   El nombre de archivo especificado en el **esquemas** campo de la ventana de propiedades de documento.  
  
-   Un esquema o DTD alineado.  
  
-   Una DTD externa o un atributo `xsd:schemaLocation` y `xsd:noNamespaceSchemaLocation`  
  
-   Un identificador URI de espacio de nombres de esquema XDR "x-schema".  
  
 También es posible encontrar esquemas en estos otros lugares cuando el esquema tiene un espacio de nombres de destino que no está vacío:  
  
-   Otra ventana del editor que contiene el esquema.  
  
-   Un esquema de la solución actual.  
  
-   Un esquema del directorio de la caché de esquema.  
  
## <a name="xslt-files"></a>Archivos XSLT  
 Al editar un archivo XSLT, se utiliza en la validación el archivo xslt.xsd ubicado en la caché de esquema. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores del compilador XSLT se muestran con un subrayado ondulado rojo.  
  
## <a name="xml-schema-xsd-files"></a>Archivos de esquema XML (XSD)  
 Al editar un archivo de esquema XML, se utiliza en la validación el archivo xsdschema.xsd ubicado en la caché de esquema. Los errores de validación se muestran con un subrayado ondulado de color azul. Los errores de compilación también se muestra con un subrayado ondulado rojo.  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)



