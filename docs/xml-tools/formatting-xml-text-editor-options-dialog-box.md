---
title: "Formato, XML, Editor de texto, Cuadro de di&#225;logo Opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Formato, XML, Editor de texto, Cuadro de di&#225;logo Opciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo permite especificar las opciones de formato del Editor XML.Puede tener acceso al cuadro de diálogo **Opciones** desde el menú **Herramientas**.  
  
> [!NOTE]
>  Estas opciones están disponibles cuando se selecciona la carpeta **Editor de texto**, la carpeta **XML** y, a continuación, la opción **Formato** del cuadro de diálogo **Opciones**.  
  
## Atributos  
 **Preservar el formato manual de atributos**  
 No se vuelve a dar formato a los atributos.Este es el valor predeterminado.  
  
> [!NOTE]
>  Si los atributos están en varias líneas, el editor aplica sangría a cada línea de atributos para que coincida con la sangría del elemento primario.  
  
 **Alinear cada atributo en su propia línea**  
 Alinea el segundo atributo y los posteriores en vertical para que coincidan con la sangría del primer atributo.La siguiente prueba XML es un ejemplo de cómo se alinearían los atributos.  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```  
  
## Formatear automáticamente  
 **Al pegar desde el Portapapeles**  
 Vuelve a dar formato al texto XML pegado desde el portapapeles.  
  
 **Al terminar la etiqueta final**  
 Vuelve a dar formato el elemento cuando se completa la etiqueta de cierre.  
  
## Contenido mixto  
 **Conservar el contenido mixto de manera predeterminada**  
 Determina si el editor volverá a dar formato al contenido mixto.De forma predeterminada, el editor intenta volver a dar formato al contenido mixto, excepto cuando el contenido se halla en un ámbito `xml:space="preserve"`.  
  
 Si un elemento contiene una mezcla de texto y marcado, se considera que el contenido es mixto.A continuación se muestra un ejemplo de un elemento con contenido mixto.  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```  
  
## Vea también  
 [Propiedades de documentos XML, Ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Componentes del Editor XML](../xml-tools/xml-editor-components.md)