---
title: Barra desplegable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0cf01e8a416407c570076812bf18aa6b21c21583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="drop-down-bar"></a>Barra de la lista desplegable
La barra de la lista desplegable se proporciona en la parte superior de la ventana de código y contiene dos listas desplegables.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barra desplegable  
 En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], por ejemplo, la barra de la lista desplegable contiene las listas de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementos y [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] funciones de miembro de los elementos, como se muestra en la siguiente imagen.  
  
 ![Quitar&#45;abajo barras](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barra de la lista desplegable  
  
 Al implementar una barra de la lista desplegable, hay cuatro interfaces de importancia principal:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implemente esta interfaz para insertar el contenido de la barra de la lista desplegable. Cada combinación de la lista desplegable puede contener texto sin formato o texto decorativo (negrita, subrayado o cursiva), puede tener el color de fuente del texto de ventana o color de fuente gris y, opcionalmente, puede proporcionar un mapa de bits pequeño situado junto al elemento de lista desplegable. Similar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz, imágenes de mapa de bits se proporcionan en listas de imágenes. Cada combinación de la lista desplegable puede tener una lista de imágenes diferentes; Sin embargo, cada lista de imágenes debe contener imágenes de la misma altura. Además, para usar el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> método, puede proporcionar información sobre herramientas para cada combinación.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Llame a esta interfaz para crear o destruir la barra de la lista desplegable de una ventana de código. Esta interfaz también puede utilizarse para determinar si una barra desplegable ya está conectada a una ventana de código mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método. Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Llame a esta interfaz para comunicarse directamente con la barra de la lista desplegable. Puede utilizar esta interfaz para forzar una actualización de la lista desplegable de la barra contenido o para cambiar la selección de uno de los cuadros de lista.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si se ha registrado el `ShowDropdownBarOption` en la clave del registro del servicio de lenguaje, a continuación, el Administrador de ventanas de código debe supervisar este evento para sincronizar con las preferencias del usuario con respecto a si se debe mostrar la barra de la lista desplegable. Si no registra esta opción en la clave del servicio de lenguaje, la opción para mostrar u ocultar la barra de la lista desplegable está deshabilitada en el **opciones** menú.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Adjuntar una barra de la lista desplegable para una ventana de código  
 Para adjuntar una barra de la lista desplegable a la ventana de código cuando se crea, un servicio de lenguaje debe asociarse a la lista desplegable barra cuando el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> se llama al método. Si una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método indica que una barra de la lista desplegable aún no existe, a continuación, llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Para tener acceso a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfaz, llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntero devuelto cuando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementación se ha adjuntado.  
  
## <a name="see-also"></a>Vea también  
 [Personalización de ventanas de código mediante la API heredado](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)