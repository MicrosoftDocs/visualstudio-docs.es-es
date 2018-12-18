---
title: Uso de marcadores de texto con la API heredada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62b77180858b40bf2620eaed284fa35b9a48288a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835935"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Uso de marcadores de texto con la API heredada
Un marcador de texto es un intervalo de texto en un búfer que puede afectar a la presentación flotante y el comportamiento de un área de texto. Los marcadores incluyen los puntos de interrupción, marcadores, subrayados ondulados y áreas de solo lectura. Marcadores de texto son básicamente diferentes colores de sintaxis. Color de la sintaxis es una manera rápida para comunicar la sintaxis del lenguaje que está asociada a un área de texto. Colorear la sintaxis generalmente se solicita cuando Windows se vuelve a dibujar la pantalla, cuando la velocidad es importante. Colorear la sintaxis cambia solo el color del texto. Marcadores de texto pueden cambiar muchas otras propiedades de texto. Marcadores de texto pueden "flotar" y aplicar un comportamiento especial y color.  
  
 Debido a la sobrecarga de rendimiento asociada con los marcadores de texto, no cree muchos marcadores para los búferes de texto. Cada marcador se actualiza cada vez que un usuario edita el contenido del búfer.  
  
> [!NOTE]
>  Los usuarios pueden cambiar el color de un tipo de marcador visible pero no su forma y estilo. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
| Título | Descripción |
| - | - |
| [Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md) | Describe cómo agregar un tipo de marcador de texto estándar proporcionado por el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básico para una vista de texto. |
| [Cómo: Implementar marcadores de error](../extensibility/how-to-implement-error-markers.md) | Describe cómo implementar una instancia de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] marcador que se usa para indicar errores mediante el uso de un subrayado ondulado rojo. |
| [Cómo: Crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md) | Describe cómo crear y agregar un tipo de marcador de texto personalizado a una vista de texto. |
| [Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md) | Explica cómo agregar marcadores de texto. |
| [Dentro del editor principal](../extensibility/inside-the-core-editor.md) | Se describen las características del editor de núcleo y proporciona detalles sobre cómo personalizar el editor básico. |
| [Características del Editor](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198) | Describe las características disponibles en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor básico. |
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Proporciona un mecanismo uniforme para obtener información sobre un tipo de marcador de texto específico, si los predefinidos por el editor o registrado por un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Proporciona acceso a y ajusta la posición de un marcador de texto en un búfer de texto mediante coordenadas bidimensionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Proporciona métodos para administrar marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Proporciona las devoluciones de llamada para el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE y otros procesos que se usan para ajustar un marcador de texto.  
  
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