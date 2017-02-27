---
title: "Uso de marcadores de texto con la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados - marcadores de texto"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Uso de marcadores de texto con la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un marcador de texto es un intervalo flotante de texto en un búfer que pueda afectar a la presentación y el comportamiento de un área de texto.  Puntos de interrupción de inclusión de los marcadores, marcadores, subrayado ondulado, y áreas de solo lectura.  Marcadores de texto son básicamente diferentes en función de la sintaxis.  El color de la sintaxis es una forma rápida de comunicar la sintaxis del lenguaje que está asociado a un área de texto.  El color de la sintaxis se solicita normalmente cuando Windows redibuja en la pantalla, cuando la velocidad es importante.  El color de la sintaxis sólo cambia el color del texto.  Marcadores de texto pueden cambiar muchas otras propiedades de texto.  Marcadores de texto pueden “float” y aplican comportamiento y color especiales.  
  
 Debido al asociado de rendimiento con marcadores de texto, no cree muchos marcadores para los búferes de texto.  Actualizan a cada marcador cada vez que un usuario edita el contenido del búfer.  
  
> [!NOTE]
>  Los usuarios pueden cambiar el color de un marcador visible tipo pero sin su forma y estilo.  Para obtener más información, vea [Fuentes y colores, Entorno, Opciones \(Cuadro de diálogo\)](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Cómo: agregar marcadores de texto estándar](../extensibility/how-to-add-standard-text-markers.md)|Describe cómo agregar un tipo de marcador de texto estándar proporcionado por el editor básico de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a una vista de texto.|  
|[Cómo: implementar marcadores de Error](../extensibility/how-to-implement-error-markers.md)|Describe cómo implementar una instancia del marcador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que se utiliza para indicar errores mediante subrayado ondulados rojos.|  
|[Cómo: crear marcadores de texto personalizado](../extensibility/how-to-create-custom-text-markers.md)|Describe cómo crear y agregar un marcador de texto personalizado escrito en una vista de texto.|  
|[Cómo: utilizar marcadores de texto](../extensibility/how-to-use-text-markers.md)|Explica cómo agregar marcadores de texto.|  
|[Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)|Describe las características del editor básico y proporciona detalles sobre cómo personalizar el editor básico.|  
|[Editor Features](http://msdn.microsoft.com/es-es/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Describe las características disponibles en el editor de la base de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .|  
  
## Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Proporciona un mecanismo uniforme para obtener más información sobre un tipo específico de marcador de texto, es predefinido por el editor o registrado por un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Proporciona acceso a y contiene la posición de un marcador de texto en un búfer de texto mediante coordenadas bidimensionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Proporciona los métodos para administrar marcadores de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Proporciona las devoluciones de llamada a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE y otros procesos que se utilizan para ajustar un marcador de texto.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Extiende la funcionalidad disponible a través de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> proporcionando devoluciones adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Extiende la funcionalidad disponible a través de la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> proporcionando devoluciones adicionales.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Permite a un tipo de marcador para determinar si otros tipos de marcador comparten el mismo conjunto de colores.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Proporciona el contexto para marcadores de texto en el editor básico.  Para cada marcador de texto escriba que esté en el editor básico, el IDE crea un objeto independiente de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un controlador que se proporciona para los marcadores cuyos glifos admiten la edición de arrastrar y colocar.  un glifo es un icono que indica la posición de un marcador.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Devuelve una interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> de un servicio que proporciona los marcadores de texto al otro VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Proporciona acceso a y contiene la posición de un marcador de texto en un búfer de texto mediante coordenadas unidimensionales.  si es posible, no utilice esta interfaz.