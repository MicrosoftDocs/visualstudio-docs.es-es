---
title: Interfaz del asistente (IDTWizard) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703275"
---
# <a name="wizard-interface-idtwizard"></a>Interfaz de asistente (IDTWizard)
El entorno de desarrollo integrado <xref:EnvDTE.IDTWizard> (IDE) utiliza la interfaz para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para poder instalarse en el IDE.

 El <xref:EnvDTE.IDTWizard.Execute%2A> método es el único <xref:EnvDTE.IDTWizard> método asociado a la interfaz. Los asistentes implementan este método y el IDE llama al método en la interfaz. En el ejemplo siguiente se muestra la firma del método.

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

 El mecanismo de inicio es similar para los asistentes **Nuevo proyecto** y Agregar **nuevo elemento.** Para iniciar cualquiera de <xref:EnvDTE.IDTWizard> ellos, llame a la interfaz definida en Dteinternal.h. La única diferencia es el conjunto de parámetros de contexto y personalizados que se pasan a la interfaz cuando se llama a la interfaz.

 La siguiente información <xref:EnvDTE.IDTWizard> describe la interfaz que los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] asistentes deben implementar para trabajar en el IDE. El IDE <xref:EnvDTE.IDTWizard.Execute%2A> llama al método en el asistente, pasándole lo siguiente:

- El objeto DTE

     El objeto DTE es la raíz del modelo de automatización.

- El identificador del cuadro de diálogo de `hwndOwner ([in] long)`la ventana como se muestra en el segmento de código, .

     El asistente `hwndOwner` lo utiliza como elemento primario para el cuadro de diálogo del asistente.

- Parámetros de contexto pasados a la interfaz como `[in] SAFEARRAY (VARIANT)* ContextParams`variante para SAFEARRAY como se muestra en el segmento de código, .

     Los parámetros de contexto contienen una matriz de valores que son específicos del tipo de asistente que se está iniciando y el estado actual del proyecto. El IDE pasa los parámetros de contexto al asistente. Para obtener más información, consulte [Parámetros de contexto](../../extensibility/internals/context-parameters.md).

- Parámetros personalizados pasados a la interfaz como variante `[in] SAFEARRAY (VARIANT)* CustomParams`para SAFEARRAY como se muestra en el segmento de código, .

     Los parámetros personalizados contienen una matriz de parámetros definidos por el usuario. Un archivo .vsz pasa parámetros personalizados al IDE. Los valores están `Param=` determinados por las instrucciones. Para obtener más información, consulte [Parámetros personalizados](../../extensibility/internals/custom-parameters.md).

- Los valores devueltos para la interfaz son

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Vea también
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
