---
title: "Validaci&#243;n de documentos XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Validaci&#243;n de documentos XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML comprueba la sintaxis XML 1.0 y realiza la validación de los datos mientras escribe.Para realizar la validación, el editor utiliza una definición de tipo de documento \(DTD\) o un esquema.Un subrayado ondulado rojo resalta los errores de XML 1.0 con un formato correcto.Un subrayado ondulado azul muestra errores semánticos basados en la validación de DTD o de esquemas.Cada error posee una entrada asociada en la lista de errores.También puede ver el mensaje de error si detiene el mouse sobre el subrayado ondulado.  
  
 Para encontrar los esquemas usados en la validación se hace coincidir el `targetNamespace` de un esquema compilado con la declaración xmlns del elemento.Los esquemas compilados se cargan desde una de las siguientes ubicaciones, mostradas en orden de prioridad:  
  
-   Desde el nombre de archivo especificado en el campo **Esquemas** de la ventana Propiedades del documento.  
  
-   Un esquema o DTD alineado.  
  
-   Una DTD externa o un atributo `xsd:schemaLocation` y `xsd:noNamespaceSchemaLocation`  
  
-   Un identificador URI de espacio de nombres de esquema XDR "x\-schema".  
  
 También es posible encontrar esquemas en estos otros lugares cuando el esquema tiene un espacio de nombres de destino que no está vacío:  
  
-   Otra ventana del editor que contiene el esquema.  
  
-   Un esquema de la solución actual.  
  
-   Un esquema del directorio de la caché de esquema.  
  
## Archivos XSLT  
 Al editar un archivo XSLT, se utiliza en la validación el archivo xslt.xsd ubicado en la caché de esquema.Los errores de validación se muestran con un subrayado ondulado de color azul.Los errores del compilador XSLT se muestran con un subrayado ondulado rojo.  
  
## Archivos de esquema XML \(XSD\)  
 Al editar un archivo de esquema XML, se utiliza en la validación el archivo xsdschema.xsd ubicado en la caché de esquema.Los errores de validación se muestran con un subrayado ondulado de color azul.Los errores de compilación también se muestra con un subrayado ondulado rojo.  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)