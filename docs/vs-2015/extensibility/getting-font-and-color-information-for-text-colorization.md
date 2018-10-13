---
title: Obtención de información de fuente y Color para la coloración de texto | Microsoft Docs
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
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7916e954079d627340a1ca41faeeadf7555acfc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274253"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtención de información de fuente y Color para la coloración de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso que se representa o muestra el texto con colores de elementos de interfaz de usuario depende del tipo de proyecto, su tecnología y desarrollador de preferencias. El **fuentes y colores** página de propiedades almacena la configuración.  
  
 La mayoría de las implementaciones que muestran texto con colores necesita el `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` y asociados de interfaces para la configuración de pantalla de presentación, recuperar y almacenar texto.  
  
> [!NOTE]
>  Al personalizar el editor básico (que admite el **texto EditorCategory**), se recomienda encarecidamente que utilice la tecnología de color en el servicio de lenguaje. Para obtener más información, consulte [información general de Color y fuente](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtención de información de Color y fuente predeterminada  
 Todas las **fuentes y colores** se debe especificar la configuración de las ventanas de mostrar texto en el **elementos para mostrar** de uno **categoría**. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para colorear, un VSPackage debe obtener actual **fuentes y colores** configuración. Un VSPackage puede hacerlo en las siguientes maneras, según sus necesidades:  
  
-   Utilice el mecanismo de persistencia de fuente y color para recuperar el estado actual o almacenado. Para obtener más información, consulte [acceso a fuente de almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfaz de un servicio que proporciona datos de fuente y color para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>si VSPackage no es también el proveedor de fuente y color.  
  
-   Implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
 Para asegurarse de que los resultados obtenidos mediante sondeo están actualizadas, puede ser útil usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaz.  
  
 Después de haber obtenido la información de fuente y color, analizar el texto que se mostrará para identificar elementos que requieren la coloración y, a continuación, muestra el texto en la ventana con las fuentes adecuadas y los colores.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilizar fuentes y texto](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabajar con colores](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (interfaz de dispositivo gráfico)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

