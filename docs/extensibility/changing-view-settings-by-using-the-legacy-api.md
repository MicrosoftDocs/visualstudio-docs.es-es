---
title: "Cambiar la configuraci&#243;n de vista mediante la API heredada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] heredados: cambiar la configuración de vista"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Cambiar la configuraci&#243;n de vista mediante la API heredada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los valores para las características básicas del editor, como el ajuste automático de línea, margen de selección, y espacio virtual, se pueden cambiar por el usuario mediante el cuadro de diálogo de **Opciones** .  Sin embargo, también es posible cambiar esta configuración mediante programación.  
  
## Cambiar la configuración mediante heredado API  
 La interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> expone un conjunto de propiedades del editor de texto.  La vista de texto contiene una categoría de propiedades \(GUID\_EditPropCategory\_View\_MasterSettings\) que representa el grupo de valores mediante programación cambiados para la vista de texto.  Los valores de la vista se ha cambiado una vez de esta manera, no se pueden cambiar en el cuadro de diálogo de **Opciones** hasta que se restablezcan.  
  
 A continuación se muestra el proceso típico para cambiar la configuración de vista para una instancia del editor básico.  
  
1.  Llame a `QueryInterface` en \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\) para la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> , especificando un valor de GUID\_EditPropCategory\_View\_MasterSettings para el parámetro de `rguidCategory` .  
  
     Esto devuelve un puntero a la interfaz de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> , que contiene el conjunto de propiedades forzadas para la vista.  Los valores en este grupo se convierten permanentemente.  Si un valor no está en este grupo, después realizará las opciones especificadas en el cuadro de diálogo de **Opciones** o los comandos de usuario.  
  
3.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> , especificando el valor apropiado de los valores del parámetro de `idprop` .  
  
     Por ejemplo, forzar el ajuste de línea, el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> de llamada y especificar un valor de VSEDITPROPID\_ViewLangOpt\_WordWrap, `vt` para el parámetro de `idprop` .  En esta llamada, `vt` es un VARIANT de VT\_BOOL escrito y `vt.boolVal` es VARIANT\_TRUE.  
  
## Restablecer valores cambiados de vista  
 Para restaurar cualquier valor cambiado de vista de una instancia del editor básico, llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> y especifique el valor adecuado del valor del parámetro de `idprop` .  
  
 Por ejemplo, permitir que el ajuste de línea flota libremente, se quitaría de la categoría de la propiedad llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> y especificando un valor de VSEDITPROPID\_ViewLangOpt\_WordWrap para el parámetro de `idprop` .  
  
 para quitar todos los valores cambiados para el editor básico inmediatamente, especifique un valor de VSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults, vt para el parámetro de `idprop` .  En esta llamada, el vt es un VARIANT de VT\_BOOL escrito y vt.boolVal es VARIANT\_TRUE.  
  
## Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Acceso a Text vista usando la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Opciones \(Cuadro de diálogo\)](../ide/reference/options-dialog-box-visual-studio.md)