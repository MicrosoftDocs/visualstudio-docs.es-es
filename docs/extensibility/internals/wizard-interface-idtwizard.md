---
title: Interfaz del asistente (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721529"
---
# <a name="wizard-interface-idtwizard"></a>Interfaz de asistente (IDTWizard)
El entorno de desarrollo integrado (IDE) utiliza la interfaz <xref:EnvDTE.IDTWizard> para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para poder instalarse en el IDE.

 El método <xref:EnvDTE.IDTWizard.Execute%2A> es el único método asociado a la interfaz <xref:EnvDTE.IDTWizard>. Los asistentes implementan este método y el IDE llama al método en la interfaz. En el ejemplo siguiente se muestra la firma del método.

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

 El mecanismo de inicio es similar para los asistentes **nuevo proyecto** y **Agregar nuevo elemento** . Para iniciar cualquiera de ellos, llame a la interfaz <xref:EnvDTE.IDTWizard> definida en Dteinternal. h. La única diferencia es el conjunto de parámetros personalizados y de contexto que se pasan a la interfaz cuando se llama a la interfaz.

 La siguiente información describe la interfaz <xref:EnvDTE.IDTWizard> que los asistentes deben implementar para trabajar en el IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El IDE llama al método <xref:EnvDTE.IDTWizard.Execute%2A> del asistente, pasándole lo siguiente:

- El objeto DTE

     El objeto DTE es la raíz del modelo de automatización.

- El identificador del cuadro de diálogo de la ventana, tal como se muestra en el segmento de código, `hwndOwner ([in] long)`.

     El asistente utiliza este `hwndOwner` como elemento primario del cuadro de diálogo del asistente.

- Los parámetros de contexto pasados a la interfaz como variante para SAFEARRAY, tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.

     Los parámetros de contexto contienen una matriz de valores que son específicos del tipo de asistente que se está iniciando y el estado actual del proyecto. El IDE pasa los parámetros de contexto al asistente. Para obtener más información, vea [parámetros de contexto](../../extensibility/internals/context-parameters.md).

- Los parámetros personalizados que se pasan a la interfaz como una variante de SAFEARRAY, tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Los parámetros personalizados contienen una matriz de parámetros definidos por el usuario. Un archivo. vsz pasa los parámetros personalizados al IDE. Los valores se determinan mediante las instrucciones `Param=`. Para obtener más información, vea [Custom Parameters](../../extensibility/internals/custom-parameters.md).

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
- [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)