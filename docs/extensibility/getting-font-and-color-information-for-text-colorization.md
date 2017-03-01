---
title: "Obtención de información de Color para los colores de texto y de fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: d0b3d50ab2a78bf806be8c7339bb260746e1c457
ms.lasthandoff: 02/22/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtención de información de Color para los colores de texto y de fuente
El proceso que se procesa o muestra el color del texto en elementos de interfaz de usuario depende del tipo de las preferencias del proyecto, su tecnología y desarrollador. El **fuentes y colores** página de propiedades almacena la configuración.  
  
 Necesita la mayoría de las implementaciones que muestran texto color el `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` y asociados de interfaces para la configuración de pantalla de presentación, recuperar y almacenar texto.  
  
> [!NOTE]
>  Al personalizar el editor principal (que es compatible con la **EditorCategory de texto**), se recomienda encarecidamente que utilice la tecnología de colores en el servicio de lenguaje. Para obtener más información, consulte [introducción de Color y fuente](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtención de información de Color y fuente predeterminada  
 Todos los **fuentes y colores** debe especificar la configuración de las ventanas de mostrar texto en el **mostrar los elementos** de uno **categoría**. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para colorear, un VSPackage debe obtener actual **fuentes y colores** configuración. Un VSPackage puede hacerlo en las siguientes formas, dependiendo de sus necesidades:  
  
-   Utilice el mecanismo de persistencia de fuente y color para recuperar el estado actual o almacenado. Para obtener más información, consulte [acceso a fuentes almacenado y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Utilice la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interfaz de un servicio que proporciona datos de color y fuente para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si el paquete VSPackage no es también el proveedor de fuente y color.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Para asegurarse de que los resultados obtenidos mediante sondeo están actualizadas, puede ser útil usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 Después de haber obtenido información de fuente y color, analizar el texto que se mostrará para identificar elementos que requieren la coloración y, a continuación, muestra el texto en la ventana con las fuentes adecuadas y los colores.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilizar fuentes y texto](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabajar con colores](/visual-cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (interfaz de dispositivo gráfico)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
