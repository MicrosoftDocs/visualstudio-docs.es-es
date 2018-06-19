---
title: Parámetros personalizados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fb61109a05b84eeb83b887ba0fc1a9f9fef299f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134352"
---
# <a name="custom-parameters"></a>Parámetros personalizados
Parámetros personalizados controlan el funcionamiento de un asistente después de que se ha iniciado un asistente. Un archivo .vsz relacionados proporciona una matriz de parámetros definidos por el usuario que se empaquetada por el entorno de desarrollo integrado (IDE) y se pasa al asistente como una matriz de cadenas cuando se inicia el asistente. A continuación, el asistente analiza la matriz de cadenas y utiliza la información para controlar la operación real del asistente. De esta manera, un asistente puede personalizar la funcionalidad según el contenido del archivo .vsz.  
  
 Parámetros de contexto, por otro lado, definen el estado del proyecto cuando se inicia el asistente. Para obtener más información, consulte [parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
 Aquí te mostramos un ejemplo de un archivo .vsz que tiene parámetros personalizados:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 El autor del archivo .vsz agrega los valores de los parámetros. Cuando un usuario selecciona **nuevo proyecto** o **Agregar nuevo elemento** en el menú archivo, o haciendo clic en un proyecto en **el Explorador de soluciones**, el IDE recopila estos valores en una matriz de cadenas. El IDE llama, a continuación, el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca conjunto y las llamadas de proyecto la <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> método que es responsable de ejecutar el asistente y devolver el resultado.  
  
 El asistente es responsable de la matriz de cadenas de análisis y actuar en las cadenas de manera apropiada. De esta manera, mediante la implementación de parámetros personalizados puede crear a un asistente que realiza una serie de funciones. En otras palabras, un asistente podría tener tres archivos .vsz diferentes. Cada archivo pasa diferentes conjuntos de parámetros personalizados para controlar el comportamiento del asistente en diversas situaciones.  
  
 Para obtener más información, vea [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)