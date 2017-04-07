---
title: "Obtener información de Color para los colores de texto y de fuente | Documentos de Microsoft"
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 57b3d53f86d132779fb00608886fa7c479b71551
ms.lasthandoff: 04/05/2017

---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtención de fuente y la información de Color para el color de texto
El proceso que se representa o se muestra texto de los elementos de interfaz de usuario depende del tipo de las preferencias del proyecto, su tecnología y developer. El **fuentes y colores** página de propiedades almacena la configuración.  
  
 Necesita la mayoría de las implementaciones que muestran texto los el `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` y asociados de interfaces para la configuración de pantalla de presentación, recuperar y almacenar texto.  
  
> [!NOTE]
>  Al personalizar el editor principal (que admite la **EditorCategory de texto**), se recomienda encarecidamente que utilice la tecnología de color en el servicio de lenguaje. Para obtener más información, consulte [introducción de Color y fuente](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtener información de Color y fuente predeterminada  
 Todas la **fuentes y colores** deben especificar los valores de las ventanas de mostrar texto en el **elementos para mostrar** de uno **categoría**. Para obtener más información, consulte [fuentes y colores, entorno, cuadro de diálogo Opciones](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para colorear, un VSPackage debe obtener actual **fuentes y colores** configuración. Un VSPackage puede hacerlo en las formas siguientes, dependiendo de sus necesidades:  
  
-   Usar el mecanismo de persistencia de fuente y color para recuperar el estado almacenado o actual. Para obtener más información, consulte [acceso a fuentes almacenados y la configuración de Color](../extensibility/accessing-stored-font-and-color-settings.md).  
  
-   Use la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interfaz de un servicio que proporciona datos de fuente y color para obtener una instancia de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, si el VSPackage no es también el proveedor de fuente y color.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
-   Implemente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
 Para asegurarse de que los resultados obtenidos mediante sondeo están actualizadas, puede ser útil usar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>interfaz para determinar si se necesita una actualización antes de llamar a los métodos de recuperación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interfaz.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
 Después de ha obtenido información de fuente y color, analice el texto que se mostrará para identificar elementos que requieren la coloración y, a continuación, muestra el texto en la ventana con las fuentes adecuadas y los colores.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Utilizar fuentes y texto](http://msdn.microsoft.com/Library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabajar con colores](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI (interfaz de dispositivo gráfico)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
