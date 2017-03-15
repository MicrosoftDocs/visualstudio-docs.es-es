---
title: "Abrir una p&#225;gina de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "abrir una página de opciones"
  - "opciones de herramientas"
  - "página de opciones"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Abrir una p&#225;gina de opciones
Puede mostrar una página de opciones mediante programación para que los usuarios de su paquete pueden configurarla durante la instalación. Para cambiar la configuración después de instalar el paquete, un usuario todavía puede obtener acceso a la página de opciones mediante el cuadro de diálogo **Opciones**.  
  
### Para mostrar una página de opciones personalizada  
  
1.  Cree una página de opciones. Para obtener más información, consulta [Crear páginas de opciones](../extensibility/internals/creating-options-pages.md).  
  
2.  Obtener el <xref:System.Type> de la página de opciones aplicando el `typeof` \(palabra clave\) en el nombre de la clase que define la página de opciones.  
  
3.  Llame al método <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> usando <xref:System.Type> de la página de opciones como parámetro.  
  
     En el ejemplo siguiente se muestra una página de opciones denominada **HelloWorldOptions**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../extensibility/internals/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../extensibility/internals/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### Para mostrar una página de opciones que se define por Visual Studio  
  
1.  En la subclave del Registro HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\, busque el nodo de la página de opciones que quiera mostrar y luego copie su GUID, que es el valor de la clave de la página.  
  
2.  Cree una instancia <xref:System.ComponentModel.Design.CommandID> que tenga las constantes <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> y <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> como parámetros.  
  
     Esto especifica el cuadro de diálogo **Opciones**.  
  
3.  Llame al método <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> con la instancia <xref:System.ComponentModel.Design.CommandID> y el GUID de cadena como parámetros.  
  
     En el ejemplo siguiente se muestra la pestaña **General** de la página de opciones **Editor de texto**.  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../extensibility/internals/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../extensibility/internals/codesnippet/VisualBasic/opening-an-options-page_2.vb)]