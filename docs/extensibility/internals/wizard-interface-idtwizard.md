---
title: Asistente para la interfaz (IDTWizard) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ebb605ed61cc06ef70fde97f3d5831c6d5c4503
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140708"
---
# <a name="wizard-interface-idtwizard"></a>Asistente para la interfaz (IDTWizard)
El entorno de desarrollo integrado (IDE) utiliza el <xref:EnvDTE.IDTWizard> interfaz para comunicarse con los asistentes. Asistentes deben implementar esta interfaz para instalarse en el IDE.  
  
 El <xref:EnvDTE.IDTWizard.Execute%2A> método es el único método asociado a la <xref:EnvDTE.IDTWizard> interfaz. Asistentes para implementan este método y el IDE llama al método en la interfaz. En el ejemplo siguiente se muestra la firma del método.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 El mecanismo de inicio es similar tanto para la **nuevo proyecto** y **Agregar nuevo elemento**asistentes. Para su inicio, se llama a la <xref:EnvDTE.IDTWizard> interfaz definida en Dteinternal.h. La única diferencia es el conjunto de contexto y parámetros personalizados que se pasan a la interfaz cuando se llama a la interfaz.  
  
 La siguiente información describe el <xref:EnvDTE.IDTWizard> interfaz que deben implementar los asistentes para trabajar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Las llamadas IDE el <xref:EnvDTE.IDTWizard.Execute%2A> método en el asistente, pasando lo siguiente:  
  
-   El objeto DTE  
  
     El objeto DTE es la raíz del modelo de automatización.  
  
-   El identificador para el cuadro de diálogo de ventana, como se muestra en el segmento de código, `hwndOwner ([in] long)`.  
  
     El asistente lo use `hwndOwner` como elemento primario para el cuadro de diálogo del asistente.  
  
-   Parámetros de contexto pasan a la interfaz como variante para SAFEARRAY tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parámetros de contexto contienen una matriz de valores que son específicas para el tipo de asistente que se inicia y el estado actual del proyecto. El IDE pasa los parámetros de contexto para el asistente. Para obtener más información, consulte [parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
-   Parámetros personalizados de pasar a la interfaz como una variante SAFEARRAY tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parámetros personalizados contienen una matriz de parámetros definidos por el usuario. Un archivo .vsz pasa parámetros personalizados para el IDE. Los valores se determinan por el `Param=` instrucciones. Para obtener más información, consulte [Custom Parameters](../../extensibility/internals/custom-parameters.md).  
  
-   Los valores devueltos para la interfaz son  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)