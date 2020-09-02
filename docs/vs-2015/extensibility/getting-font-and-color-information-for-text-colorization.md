---
title: Obtención de información de fuente y color para la coloración del texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696857"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtención de información sobre fuentes y colores para la coloración de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso que representa o muestra texto coloreado en elementos de la interfaz de usuario (IU) depende del tipo de proyecto, su tecnología y sus preferencias de desarrollador. La página de propiedades **fuentes y colores** almacena la configuración.  
  
 La mayoría de las implementaciones que muestran texto coloreado necesitan las `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaces asociadas y para presentar, recuperar y almacenar la configuración de presentación de texto.  
  
> [!NOTE]
> Al personalizar el editor básico (que admite el **texto EditorCategory**), se recomienda encarecidamente que utilice la tecnología de color en el servicio de lenguaje. Para obtener más información, vea [información general sobre fuentes y colores](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtención de la información de fuente y color predeterminada  
 Toda la configuración de **fuentes y colores** de cualquier ventana que muestre texto debe especificarse en los **elementos para mostrar** de una **categoría**. Para obtener más información, vea [fuentes y colores, entorno, opciones (cuadro de diálogo](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)).  
  
 Para colorear, un VSPackage debe obtener la configuración actual **de fuentes y colores** . Un VSPackage puede conseguirlo de las siguientes maneras, en función de sus necesidades:  
  
- Use el mecanismo de persistencia de fuente y color para recuperar el estado almacenado o actual. Para obtener más información, vea [acceso a la configuración de fuente y color almacenados](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz de un servicio que proporciona datos de fuente y color para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , si el VSPackage no es también el proveedor de fuente y color.  
  
- Implemente la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Para asegurarse de que los resultados obtenidos mediante el sondeo están actualizados, puede ser útil usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
  Después de obtener la información de fuente y color, analice el texto que se va a mostrar para identificar los elementos que requieren coloración y, a continuación, muestre el texto en la ventana con las fuentes y los colores apropiados.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Usar fuentes y texto](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabajar con colores](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (interfaz de dispositivo gráfico)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
