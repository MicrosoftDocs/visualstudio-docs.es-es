---
title: Interfaz del asistente (IDTWizard) | Microsoft Docs
description: El IDE usa la interfaz IDTWizard para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para que se instale en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898622"
---
# <a name="wizard-interface-idtwizard"></a>Interfaz de asistente (IDTWizard)
El entorno de desarrollo integrado (IDE) usa la <xref:EnvDTE.IDTWizard> interfaz para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para poder instalarse en el IDE.

 El <xref:EnvDTE.IDTWizard.Execute%2A> método es el único método asociado a la interfaz <xref:EnvDTE.IDTWizard> . Los asistentes implementan este método y el IDE llama al método en la interfaz . En el ejemplo siguiente se muestra la firma del método .

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

 El mecanismo de inicio es similar para los asistentes **Nuevo proyecto** y **Agregar nuevo** elemento. Para empezar, llame a la <xref:EnvDTE.IDTWizard> interfaz definida en Dteinternal.h. La única diferencia es el conjunto de parámetros de contexto y personalizados que se pasan a la interfaz cuando se llama a la interfaz.

 En la siguiente información se describe la <xref:EnvDTE.IDTWizard> interfaz que los asistentes deben implementar para que funcione en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. El IDE llama al <xref:EnvDTE.IDTWizard.Execute%2A> método en el asistente y le pasa lo siguiente:

- El objeto DTE

     El objeto DTE es la raíz del modelo de Automation.

- Identificador del cuadro de diálogo de ventana, como se muestra en el segmento de código, `hwndOwner ([in] long)` .

     El asistente lo usa `hwndOwner` como elemento primario del cuadro de diálogo del asistente.

- Parámetros de contexto pasados a la interfaz como variant para SAFEARRAY, como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Los parámetros de contexto contienen una matriz de valores que son específicos del tipo de asistente que se inicia y el estado actual del proyecto. El IDE pasa los parámetros de contexto al asistente. Para obtener más información, vea [Parámetros de contexto.](../../extensibility/internals/context-parameters.md)

- Parámetros personalizados pasados a la interfaz como una variante para SAFEARRAY, como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Los parámetros personalizados contienen una matriz de parámetros definidos por el usuario. Un archivo .vsz pasa parámetros personalizados al IDE. Los valores se determinan mediante `Param=` las instrucciones . Para obtener más información, vea [Parámetros personalizados.](../../extensibility/internals/custom-parameters.md)

- Los valores devueltos para la interfaz son:

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Consulta también
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
