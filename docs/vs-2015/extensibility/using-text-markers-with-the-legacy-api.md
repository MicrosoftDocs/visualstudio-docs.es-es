---
title: Uso de marcadores de texto con la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f863571672c42f63912629844fd72d8c92ca8400
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263671"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Uso de marcadores de texto con la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marcador de texto es un intervalo de texto en un búfer que puede afectar a la presentación flotante y el comportamiento de un área de texto. Los marcadores incluyen los puntos de interrupción, marcadores, subrayados ondulados y áreas de solo lectura. Marcadores de texto son básicamente diferentes colores de sintaxis. Color de la sintaxis es una manera rápida para comunicar la sintaxis del lenguaje que está asociada a un área de texto. Colorear la sintaxis generalmente se solicita cuando Windows se vuelve a dibujar la pantalla, cuando la velocidad es importante. Colorear la sintaxis cambia solo el color del texto. Marcadores de texto pueden cambiar muchas otras propiedades de texto. Marcadores de texto pueden "flotar" y aplicar un comportamiento especial y color.  
  
 Debido a la sobrecarga de rendimiento asociada con los marcadores de texto, no cree muchos marcadores para los búferes de texto. Cada marcador se actualiza cada vez que un usuario edita el contenido del búfer.  
  
> [!NOTE]
>  Los usuarios pueden cambiar el color de un tipo de marcador visible pero no su forma y estilo. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)|Describe cómo agregar un tipo de marcador de texto estándar proporcionado por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor básico para una vista de texto.|  
|[Cómo: Implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)|Describe cómo implementar una instancia de la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marcador que se usa para indicar errores mediante el uso de un subrayado ondulado rojo.|  
|[Cómo: Crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)|Describe cómo crear y agregar un tipo de marcador de texto personalizado a una vista de texto.|  
|[Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)|Explica cómo agregar marcadores de texto.|  
|[Dentro del editor principal](../extensibility/inside-the-core-editor.md)|Se describen las características del editor de núcleo y proporciona detalles sobre cómo personalizar el editor básico.|  
|[Características del Editor](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Describe las características disponibles en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor básico.|  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Proporciona un mecanismo uniforme para obtener información sobre un tipo de marcador de texto específico, si los predefinidos por el editor o registrado por un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Proporciona acceso a y ajusta la posición de un marcador de texto en un búfer de texto mediante coordenadas bidimensionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Proporciona métodos para administrar marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Proporciona las devoluciones de llamada para el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE y otros procesos que se usan para ajustar un marcador de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Extiende la funcionalidad que está disponible a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz proporcionando las devoluciones de llamada adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Extiende la funcionalidad que está disponible a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz proporcionando las devoluciones de llamada adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permite un tipo de marcador determinar si otros tipos de marcador comparten el mismo conjunto de colores.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Proporciona contexto para los marcadores de texto en el editor básico. Para cada tipo de marcador de texto que se encuentra en el editor básico, el IDE crea otro <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objeto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un controlador que se proporciona para los marcadores cuyos glifos admiten la edición de arrastrar y colocar. Un glifo es un icono que indica la posición de un marcador.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Devuelve un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaz desde un servicio que proporciona un texto de los marcadores de otros VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Proporciona acceso a y ajusta la posición de un marcador de texto en un búfer de texto mediante coordenadas unidimensionales. Si es posible, no utilice esta interfaz.

