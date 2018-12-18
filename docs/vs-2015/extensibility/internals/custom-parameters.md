---
title: Parámetros personalizados | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8bb8a1861d6162e73906d74250f738ff96b9a505
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757903"
---
# <a name="custom-parameters"></a>Parámetros personalizados
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parámetros personalizados controlan el funcionamiento de un asistente después de que se ha iniciado un asistente. Un archivo .vsz relacionados proporciona una matriz de parámetros definido por el usuario que se empaquetan en el entorno de desarrollo integrado (IDE) y se pasa al asistente como una matriz de cadenas cuando se inicia el asistente. A continuación, el asistente analiza la matriz de cadenas y usa la información para controlar la operación real del asistente. De esta manera, un asistente puede personalizar la funcionalidad según el contenido del archivo .vsz.  
  
 Parámetros de contexto, por otro lado, definen el estado del proyecto cuando se inicia el asistente. Para obtener más información, consulte [parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
 Este es un ejemplo de un archivo .vsz que tiene parámetros personalizados:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 El autor del archivo .vsz agrega los valores de los parámetros. Cuando un usuario selecciona **nuevo proyecto** o **Agregar nuevo elemento** en el menú archivo o con el botón secundario en un proyecto de **el Explorador de soluciones**, el IDE recopila estos valores en una matriz de cadenas. El IDE, a continuación, llama el proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca conjunto y las llamadas de proyecto la <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> método que es responsable de ejecutar el asistente y devolviendo el resultado.  
  
 El asistente es responsable de la matriz de cadenas de análisis y actuar sobre las cadenas de manera apropiada. De esta manera, mediante la implementación de parámetros personalizados puede crear a un asistente que realiza una serie de funciones. En otras palabras, un asistente podría tener tres archivos .vsz diferentes. Cada archivo pasa a diferentes conjuntos de parámetros personalizados para controlar el comportamiento del asistente en diversas situaciones.  
  
 Para obtener más información, consulte [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

