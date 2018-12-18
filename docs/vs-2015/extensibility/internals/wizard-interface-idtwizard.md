---
title: Interfaz de asistente (IDTWizard) | Documentos de Microsoft
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
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62ae4ab1137be452a1c769d16c153e4499a4a331
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792533"
---
# <a name="wizard-interface-idtwizard"></a>Interfaz de asistente (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El entorno de desarrollo integrado (IDE) utiliza el <xref:EnvDTE.IDTWizard> interfaz para comunicarse con los asistentes. Asistentes deben implementar esta interfaz para instalarse en el IDE.  
  
 El <xref:EnvDTE.IDTWizard.Execute%2A> método es el único método asociado con el <xref:EnvDTE.IDTWizard> interfaz. Los asistentes implementan este método y el IDE llama al método en la interfaz. El ejemplo siguiente muestra la firma del método.  
  
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
  
 El mecanismo de inicio es similar para ambos el **nuevo proyecto** y **Agregar nuevo elemento**asistentes. Para empezar a cualquiera, llame a la <xref:EnvDTE.IDTWizard> interfaz definida en Dteinternal.h. La única diferencia es el conjunto de contexto y los parámetros personalizados que se pasan a la interfaz cuando se llama a la interfaz.  
  
 La siguiente información describe la <xref:EnvDTE.IDTWizard> interfaz que deben implementar los asistentes para trabajar en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Las llamadas IDE el <xref:EnvDTE.IDTWizard.Execute%2A> método en el asistente, pasa lo siguiente:  
  
-   El objeto DTE  
  
     El objeto DTE es la raíz del modelo de automatización.  
  
-   El identificador para el cuadro de diálogo de ventana, como se muestra en el segmento de código, `hwndOwner ([in] long)`.  
  
     El asistente usa esto `hwndOwner` como el elemento primario de cuadro de diálogo del asistente.  
  
-   Parámetros de contexto de pasar a la interfaz como variante SAFEARRAY tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parámetros de contexto contienen una matriz de valores que son específicas del tipo de asistente que se está iniciando y el estado actual del proyecto. El IDE pasa los parámetros de contexto al asistente. Para obtener más información, consulte [parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
-   Parámetros personalizados de pasar a la interfaz como una variante SAFEARRAY tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parámetros personalizados contienen una matriz de parámetros definido por el usuario. Un archivo .vsz pasa parámetros personalizados en el IDE. Los valores se determinan por el `Param=` instrucciones. Para obtener más información, consulte [parámetros personalizados](../../extensibility/internals/custom-parameters.md).  
  
-   Valores devueltos para la interfaz son  
  
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

