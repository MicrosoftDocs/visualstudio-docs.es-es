---
title: "Elemento de mapa de bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, mapas de bits"
  - "Elemento de mapas de bits (esquema VSCT XML)"
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento de mapa de bits
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo.  
  
## Sintaxis  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. GUID del identificador de comando\/identificador GUID.<br /><br /> El atributo de guid para un mapa de bits no está asociado con cualquier VSPackage u otro grupo de comandos.  Debe ser único en la definición de mapa de bits y no debe utilizarse para ningún otro propósito.|  
|resID|Id. del identificador de comando\/identificador GUID. Se requiere el resID o el atributo href.<br /><br /> El atributo resID es un identificador de recurso de entero que determina la franja de mapa de bits que debe cargarse durante la combinación de tabla de comandos.  Cuando se carga la tabla de comandos, se cargarán los mapas de bits especificado por el identificador de recursos desde el recurso del mismo módulo.|  
|usedList|Requerido si está presente el atributo resID. Selecciona las imágenes disponibles en la franja de mapa de bits.|  
|href|Ruta de acceso al mapa de bits. Se requiere el resID o el atributo href.<br /><br /> La ruta de acceso de inclusión se busca el archivo de imagen indicado, que está incrustado en el binario resultante.  Durante la combinación de tabla de comandos, se copia la imagen y no se requiere ninguna búsqueda de recursos adicionales o carga.  Si no está presente el atributo usedList, están disponibles todas las imágenes de la franja. **Note:**  Uno de los diversos formatos que incluyen .bmp, .png y .gif se suministran imágenes.  Las versiones anteriores del compilador no era compatible con imágenes de mapa de bits de 32 bits que contiene información alfa para la transparencia parcial. La solución para estas versiones es utilizar el formato PNG.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de mapas de bits](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|  
  
## Ejemplo  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" /> <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS" usedList="1, 2, 3, 4"/>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)