---
title: Barra desplegable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a23249a80b87c55e3065abb7cca192182aad4fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968068"
---
# <a name="drop-down-bar"></a>Barra desplegable
La barra desplegable se proporciona en la parte superior de la ventana de código y contiene dos listas desplegables.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barra desplegable  
 En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], por ejemplo, la barra de la lista desplegable contiene listas para [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] elementos y [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] funciones miembro de los elementos, como se muestra en la siguiente imagen.  
  
 ![Quitar&#45;abajo barras](../extensibility/media/vsdropdown_bar.gif "vsDropdown_bar")  
Barra desplegable  
  
 Al implementar una barra desplegable, hay cuatro interfaces de importancia primordial:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implemente esta interfaz para insertar el contenido de la barra desplegable. Cada combinación de la lista desplegable puede contener texto sin formato o texto decorativo (negrita, subrayado o cursiva), puede tener el color de fuente del texto de ventana o color de fuente gris y, opcionalmente, puede proporcionar un mapa de bits pequeño situado junto al elemento de lista desplegable. Similar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz, las imágenes de mapa de bits se proporcionan en las listas de imágenes. Cada combinación de la lista desplegable puede tener una lista de imágenes diferentes; Sin embargo, cada lista de imágenes debe contener las imágenes de la misma altura. Además, el uso de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> método, puede proporcionar información sobre herramientas para cada combinación.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Llame a esta interfaz para crear o destruir la barra desplegable para una ventana de código. También puede utilizarse para determinar si una barra desplegable ya está asociada a una ventana de código mediante una llamada a esta interfaz la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método. Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> desde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Llame a esta interfaz para comunicarse directamente con la barra desplegable. Puede usar esta interfaz para forzar una actualización de la lista desplegable de la barra contenido o para cambiar la selección de uno de los cuadros de lista.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si se ha registrado el `ShowDropdownBarOption` en la clave del registro del servicio de lenguaje, a continuación, el Administrador de ventanas de código debe supervisar este evento para sincronizar con las preferencias del usuario con respecto a si se debe mostrar la barra desplegable. Si no registra esta opción en la clave de servicio de lenguaje, a continuación, la opción para mostrar u ocultar la barra desplegable está deshabilitada en el **opciones** menú.  
  
## <a name="attach-a-drop-down-bar-to-a-code-window"></a>Adjuntar una barra desplegable a una ventana de código  
 Para adjuntar una barra desplegable a la ventana de código cuando se crea, un servicio de lenguaje se debe asociar a la lista desplegable barra cuando el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> se llama al método. Si una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método indica que una barra desplegable ya no existe, a continuación, llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>. Para tener acceso a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfaz, llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntero devuelto cuando su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> implementación se ha adjuntado.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar las ventanas de código mediante el uso de la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)