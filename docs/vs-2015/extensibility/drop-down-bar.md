---
title: Barra desplegable | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204658"
---
# <a name="drop-down-bar"></a>Barra desplegable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La barra desplegable se proporciona en la parte superior de la ventana de código y contiene dos listas desplegables.  
  
## <a name="drop-down-bar-interfaces"></a>Interfaces de barra desplegable  
 En [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , por ejemplo, la barra desplegable contiene listas de [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] funciones de miembro de elementos y [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] elementos, tal como se muestra en la siguiente imagen.  
  
 ![Quitar&#45;barras descendentes](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Barra desplegable  
  
 Al implementar una barra desplegable, hay cuatro interfaces de importancia principal:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Implemente esta interfaz para insertar el contenido de la barra desplegable. Cada combinación desplegable puede contener texto sin formato o texto decorativo (negrita, subrayado o cursiva), puede tener un color de fuente de texto de ventana o un color de fuente atenuado y, opcionalmente, puede proporcionar un mapa de bits pequeño junto al elemento desplegable. De forma similar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaz, las imágenes de mapa de bits se proporcionan en las listas de imágenes. Cada combinación desplegable puede tener una lista de imágenes diferente. sin embargo, cada lista de imágenes debe contener imágenes del mismo alto. Además, con el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> método, puede proporcionar una información sobre herramientas para cada combinación.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Llame a esta interfaz para crear o destruir la barra desplegable de una ventana de código. Esta interfaz también se puede utilizar para determinar si una barra desplegable ya está adjunta a una ventana de código mediante una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método. Llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> desde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Llame a esta interfaz para comunicarse directamente con la barra desplegable. Puede utilizar esta interfaz para forzar una actualización del contenido de la barra desplegable o para cambiar la selección en uno de los cuadros de lista.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si ha registrado el `ShowDropdownBarOption` en la clave del registro del servicio de lenguaje, el administrador de ventanas de código debe supervisar este evento para sincronizar con las preferencias del usuario con respecto a si se debe mostrar la barra desplegable. Si no registra esta opción en la clave del servicio de lenguaje, se deshabilitará la opción para mostrar u ocultar la barra desplegable en el menú **Opciones** .  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Adjuntar una barra desplegable a una ventana de código  
 Para adjuntar una barra desplegable a la ventana de código cuando se crea, un servicio de lenguaje se debe adjuntar a la barra desplegable cuando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> se llama al método. Si una llamada al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> método indica que no existe ya una barra desplegable, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . Para tener acceso a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> interfaz, llame a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> puntero que se le devolvió cuando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> se adjuntó la implementación.  
  
## <a name="see-also"></a>Consulte también  
 [Personalización de ventanas de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
