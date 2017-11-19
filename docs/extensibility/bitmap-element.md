---
title: Elemento de mapa de bits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 223342709dbe97fe38fb7a495ce482ae70e1c807
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="bitmap-element"></a>Elemento de mapa de bits
Define un mapa de bits. El mapa de bits se carga desde un recurso o desde un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|guid|Obligatorio. GUID del identificador de comando/identificador GUID.<br /><br /> El atributo guid de un mapa de bits no está asociado con cualquier VSPackage u otro grupo de comandos.  Debe ser único para la definición de mapa de bits y no debe usarse para ningún otro propósito.|  
|resID|Id. del identificador de comando/identificador GUID. Se requiere el resID o el atributo href.<br /><br /> El atributo resID es un identificador de recurso de entero que determina la franja de mapa de bits que debe cargarse durante la tabla de comandos de combinación.  Cuando se carga la tabla de comandos, los mapas de bits especificado por el identificador de recurso se cargará desde el recurso del mismo módulo.|  
|usedList|Obligatorio si está presente el atributo resID. Selecciona las imágenes disponibles en la franja de mapa de bits.|  
|href|Ruta de acceso al mapa de bits. Se requiere el resID o el atributo href.<br /><br /> La ruta de acceso de inclusión se busca el archivo de imagen indicado, que está incrustado en el binario resultante.  Durante la combinación de tabla de comandos, se copia la imagen y no se requiere ninguna búsqueda de recursos adicionales o carga.  Si no está presente el atributo usedList, están disponibles todas las imágenes en la franja. **Nota:** imágenes pueden proporcionarse en uno de los distintos formatos que incluyen .bmp, .png y .gif.  Las versiones anteriores del compilador no era compatible con imágenes de mapa de bits de 32 bits que tenían información alfa para la transparencia parcial. La solución para estas versiones es utilizar el formato. png.|  
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Bitmaps (Elemento)](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)