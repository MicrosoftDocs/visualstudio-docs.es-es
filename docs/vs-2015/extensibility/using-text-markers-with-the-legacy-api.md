---
title: Uso de marcadores de texto con la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dff5e6ecf60d389730841e99b87db584465e020
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695478"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Uso de marcadores de texto con la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un marcador de texto es un intervalo flotante de texto en un búfer que puede afectar a la presentación y el comportamiento de una región de texto. Entre los marcadores se incluyen los puntos de interrupción, los marcadores, los subrayados ondulados y las áreas de solo lectura. Los marcadores de texto son básicamente distintos de los colores de la sintaxis. El color de la sintaxis es una forma rápida de comunicar la sintaxis del lenguaje que está asociada a una región de texto. El color de la sintaxis suele solicitarse cuando Windows vuelve a dibujar la pantalla, cuando la velocidad es importante. El coloreado de la sintaxis solo cambia el color del texto. Los marcadores de texto pueden cambiar muchas otras propiedades de texto. Los marcadores de texto pueden "flotar" y aplicar el comportamiento y el color especiales.  
  
 Debido a la sobrecarga de rendimiento asociada a los marcadores de texto, no cree muchos marcadores para los búferes de texto. Cada marcador se actualiza cada vez que un usuario edita el contenido del búfer.  
  
> [!NOTE]
> Los usuarios pueden cambiar el color de un tipo de marcador visible, pero no su forma y estilo. Para obtener más información, vea [fuentes y colores, entorno, opciones (cuadro de diálogo](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Cómo: Agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)|Describe cómo agregar un tipo de marcador de texto estándar proporcionado por el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal a una vista de texto.|  
|[Cómo: Implementar marcadores de error](../extensibility/how-to-implement-error-markers.md)|Describe cómo implementar una instancia del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] marcador que se usa para indicar errores mediante el uso de subrayado ondulado rojo.|  
|[Cómo: Crear marcadores de texto personalizados](../extensibility/how-to-create-custom-text-markers.md)|Describe cómo crear y agregar un tipo de marcador de texto personalizado a una vista de texto.|  
|[Cómo: Usar marcadores de texto](../extensibility/how-to-use-text-markers.md)|Explica cómo agregar marcadores de texto.|  
|[Dentro del editor principal](../extensibility/inside-the-core-editor.md)|Describe las características del editor básico y proporciona detalles sobre cómo personalizar el editor básico.|  
|[Características del editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Describe las características disponibles en el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor básico.|  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Proporciona un mecanismo uniforme para obtener información sobre un tipo de marcador de texto concreto, ya sea predefinido por el editor o registrado por un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Proporciona acceso y ajusta la posición de un marcador de texto en un búfer de texto mediante el uso de coordenadas bidimensionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Proporciona métodos para administrar marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Proporciona devoluciones de llamada al [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE y a otros procesos que se usan para ajustar un marcador de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Extiende la funcionalidad que está disponible a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz proporcionando devoluciones de llamada adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Extiende la funcionalidad que está disponible a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interfaz proporcionando devoluciones de llamada adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Habilita un tipo de marcador para determinar si otros tipos de marcadores comparten el mismo conjunto de colores.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Proporciona el contexto de los marcadores de texto en el editor básico. Para cada tipo de marcador de texto que se encuentra en el editor principal, el IDE crea un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objeto independiente.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Controlador que se proporciona para los marcadores cuyos glifos admiten la edición de arrastrar y colocar. Un glifo es un icono que indica la posición de un marcador.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Devuelve una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> interfaz de un servicio que proporciona marcadores de texto a otros VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Proporciona acceso y ajusta la posición de un marcador de texto en un búfer de texto mediante el uso de coordenadas unidimensionales. Si es posible, no utilice esta interfaz.
