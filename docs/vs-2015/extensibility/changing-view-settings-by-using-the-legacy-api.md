---
title: Cambiar la configuración de vista mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184463"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Cambio de la configuración de vista mediante la API heredada API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El usuario puede cambiar la configuración de las características principales del editor, como el ajuste de palabras, el margen de selección y el espacio virtual, por medio del cuadro de diálogo **Opciones** . Sin embargo, también es posible cambiar esta configuración mediante programación.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Cambiar la configuración mediante la API heredada  
 La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz expone un conjunto de propiedades del editor de texto. La vista de texto contiene una categoría de propiedades (GUID_EditPropCategory_View_MasterSettings) que representa el grupo de valores de configuración cambiados mediante programación para la vista de texto. Una vez que se ha cambiado la configuración de la vista de esta manera, no se pueden cambiar en el cuadro de diálogo **Opciones** hasta que se restablezcan.  
  
 A continuación se muestra el proceso típico para cambiar la configuración de vista de una instancia del editor básico.  
  
1. Llame a `QueryInterface` en el ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> ) para la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz.  
  
2. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método, especificando un valor de GUID_EditPropCategory_View_MasterSettings para el `rguidCategory` parámetro.  
  
     Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz, que contiene el conjunto de propiedades forzadas para la vista. Cualquier configuración de este grupo se fuerza de forma permanente. Si un valor no se encuentra en este grupo, se seguirán las opciones especificadas en el cuadro de diálogo **Opciones** o los comandos del usuario.  
  
3. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> método, especificando el valor de configuración adecuado en el `idprop` parámetro.  
  
     Por ejemplo, para forzar el ajuste de palabras, llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> y especifique un valor de VSEDITPROPID_ViewLangOpt_WordWrap `vt` para el `idprop` parámetro. En esta llamada, `vt` es una variante de tipo VT_BOOL y `vt.boolVal` se VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Restableciendo la configuración de vista modificada  
 Para restablecer la configuración de vista modificada de una instancia del editor principal, llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> método y especifique el valor de configuración adecuado en el `idprop` parámetro.  
  
 Por ejemplo, para permitir que el ajuste de palabra flote libremente, debe quitarlo de la categoría de propiedad llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> y especificando un valor de VSEDITPROPID_ViewLangOpt_WordWrap para el `idprop` parámetro.  
  
 Para quitar toda la configuración modificada del editor principal a la vez, especifique un valor de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, VT para el `idprop` parámetro. En esta llamada, VT es una variante del tipo VT_BOOL y se VARIANT_TRUE VT. boolVal.  
  
## <a name="see-also"></a>Consulte también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)   
 [Obtener acceso a la vista de texto mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Cuadro de diálogo Opciones](../ide/reference/options-dialog-box-visual-studio.md)
