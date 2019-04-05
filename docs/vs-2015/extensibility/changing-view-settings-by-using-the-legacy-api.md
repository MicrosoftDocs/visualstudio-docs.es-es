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
ms.openlocfilehash: ddca5f9159c2cb20eeb8525bd37730a88f64fb43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995527"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>Cambie la configuración de vista mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Configuración de las características del editor de núcleo, como el ajuste de palabra, margen de selección y el espacio virtual, puede cambiarse por el usuario por medio de la **opciones** cuadro de diálogo. Sin embargo, también es posible cambiar esta configuración mediante programación.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>Cambiar la configuración mediante la API heredada  
 El <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz expone un conjunto de propiedades del editor de texto. La vista de texto contiene una categoría de propiedades (GUID_EditPropCategory_View_MasterSettings) que representa el grupo de configuración mediante programación modificada para la vista de texto. Una vez que la configuración de la vista se han cambiado en este modo, no puede cambiarse en el **opciones** cuadro de diálogo hasta que se restablecen.  
  
 Siguiente es el proceso típico para cambiar la configuración de vista para una instancia del editor de núcleo.  
  
1.  Llame a `QueryInterface` en el (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) para el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método, especificando un valor de GUID_EditPropCategory_View_MasterSettings para el `rguidCategory` parámetro.  
  
     Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaz, que contiene el conjunto de propiedades forzadas de la vista. Permanentemente se fuerza la cualquier configuración de este grupo. Si una configuración no está en este grupo, seguirá las opciones especificadas en el **opciones** cuadro de diálogo o los comandos del usuario.  
  
3.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> método, especificando el valor de la configuración adecuada en el `idprop` parámetro.  
  
     Por ejemplo, para forzar ajuste, llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> y especifique un valor de VSEDITPROPID_ViewLangOpt_WordWrap, `vt` para el `idprop` parámetro. En esta llamada, `vt` es una variante de tipo VT_BOOL y `vt.boolVal` es VARIANT_TRUE.  
  
## <a name="resetting-changed-view-settings"></a>Restablecer la configuración de vista modificado  
 Para restablecer cualquier vista modificada para una instancia del editor de núcleo, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> método y especificar el valor de la configuración adecuada en el `idprop` parámetro.  
  
 Por ejemplo, para permitir el ajuste de línea flotar libremente, lo haría quita de la categoría de propiedad mediante una llamada a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> y especificando un valor de VSEDITPROPID_ViewLangOpt_WordWrap para el `idprop` parámetro.  
  
 Para quitar la configuración de todo esto cambió para el editor básico a la vez, especifique un valor de VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt para el `idprop` parámetro. En esta llamada, vt es una variante de tipo VT_BOOL y vt.boolVal es VARIANT_TRUE.  
  
## <a name="see-also"></a>Vea también  
 [En el Editor básico](../extensibility/inside-the-core-editor.md)   
 [Acceso a Text vista mediante la API heredada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [Opciones (cuadro de diálogo)](../ide/reference/options-dialog-box-visual-studio.md)
