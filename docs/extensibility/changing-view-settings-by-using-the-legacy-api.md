---
title: "Cambiar la configuración de la vista mediante la API heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc68bf5f8a0e61b80200cd5454b78bcdda78cdfe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Cambiar la configuración de la vista mediante la API heredado
Configuración de características del editor principal, como el ajuste automático de línea, el margen de selección y el espacio virtual, se puede modificar por el usuario por medio de la **opciones** cuadro de diálogo. Sin embargo, también es posible cambiar esta configuración mediante programación.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Cambiar la configuración mediante la API heredado  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz expone un conjunto de propiedades del editor de texto. La vista de texto contiene una categoría de propiedades (GUID_EditPropCategory_View_MasterSettings) que representa el grupo de configuración mediante programación modificada para la vista de texto. Una vez que se cambiaron ver la configuración de esta manera, no se puede cambiar en el **opciones** cuadro de diálogo hasta que se restablecen.  
  
 Aquí te mostramos el proceso típico para cambiar la configuración de vista para una instancia del editor principal.  
  
1.  Llame a `QueryInterface` en el (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método, especificando un valor de GUID_EditPropCategory_View_MasterSettings para el `rguidCategory` parámetro.  
  
     Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz, que contiene el conjunto de propiedades forzadas para la vista. Cualquier configuración de este grupo de forma permanente se convierten obligatoriamente. Si una configuración no está en este grupo, se seguirá las opciones especificadas en el **opciones** cuadro de diálogo o los comandos del usuario.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> método, especificando el valor de la configuración adecuada en la `idprop` parámetro.  
  
     Por ejemplo, para forzar ajuste automático de línea, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> y especifique un valor de VSEDITPROPID_ViewLangOpt_WordWrap, `vt` para el `idprop` parámetro. En esta llamada, `vt` es una variante del tipo VT_BOOL y `vt.boolVal` es VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Restablecer la configuración de vista modificada  
 Para restablecer cualquier configuración para una instancia del editor principal de la vista modificada, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> método y especifique el valor de configuración adecuado en el `idprop` parámetro.  
  
 Por ejemplo, para permitir el ajuste de línea flotar libremente, se podría quitar de la categoría de propiedad llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> y especificando un valor de VSEDITPROPID_ViewLangOpt_WordWrap para el `idprop` parámetro.  
  
 Para quitar configuración de todos los modificada para el editor principal a la vez, especifique un valor de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt para el `idprop` parámetro. En esta llamada, vt es una variante del tipo VT_BOOL y vt.boolVal es VARIANT_TRUE.  
  
## <a name="see-also"></a>Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Obtener acceso a Text vista mediante la API heredado](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Opciones (cuadro de diálogo)](../ide/reference/options-dialog-box-visual-studio.md)