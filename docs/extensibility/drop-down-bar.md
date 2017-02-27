---
title: "Barra desplegable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "heredado de editores [Visual Studio SDK], - lista desplegable de la barra"
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Barra desplegable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La barra desplegable se proporciona en la parte superior de la ventana de código y contiene dos listas desplegables.  
  
## Interfaces desplegables de barra  
 En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], por ejemplo, la barra desplegable contiene las listas de elementos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] y el miembro de los elementos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] funciona, como se muestra en la siguiente imagen.  
  
 ![Barras desplegables](../extensibility/media/vsdropdown_bar.gif "vsDropdown\_bar")  
barra desplegable  
  
 Al implementar una barra desplegable, hay cuatro interfaces de importancia principal:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     implemente esta interfaz para insertar el contenido de la barra desplegable.  Cada combinación desplegable puede contener texto sin formato o el texto de lujo \(negrita, subrayado, o en cursiva\), puede tener el color de la fuente del texto de la ventana o out atenuado colorear la fuente, y puede proporcionar un mapa de bits junto al elemento desplegable.  Similar a la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> , imágenes de mapa de bits se proporcionan en listas de imágenes.  Cada combinación desplegable puede tener otra lista de imágenes; sin embargo, cada lista de imagen debe contener imágenes del mismo alto.  Además, mediante el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> , puede proporcionar una información sobre herramientas para cada combinación.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Llame a esta interfaz al crear o se destruye la barra desplegable para una ventana de código.  Esta interfaz se puede utilizar para determinar si una barra desplegable está adjunta ya a una ventana de código llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> .  llamada <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Llame a esta interfaz para comunicarse directamente con la barra desplegable.  Puede utilizar esta interfaz para forzar una actualización del contenido desplegables de la barra o cambiar la selección en uno de los cuadros de lista.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     Si ha registrado `ShowDropdownBarOption` en la clave del Registro del servicio de lenguaje, el administrador de ventanas de códigos debe controlar este evento para sincronizar con las preferencias del usuario en relación con si la barra desplegable debe mostrar.  Si no registra esta opción en la clave del servicio de lenguaje, la opción de mostrar u ocultar la barra desplegable está deshabilitado en el menú de **Opciones** .  
  
## Adjuntar una barra desplegable a una ventana de código  
 Para adjuntar una barra desplegable a la ventana de código cuando se crea, un servicio de lenguaje debe adjuntar la barra desplegable cuando se llama al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> .  Si una llamada al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> indica que no existe una barra desplegable ya, llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A>.  Para tener acceso a la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> , la llamada <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> de puntero de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> devueltos a se cuando la implementación de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> se adjunta.  
  
## Vea también  
 [Personalización de Windows de código mediante la API heredada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)