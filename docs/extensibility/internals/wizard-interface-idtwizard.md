---
title: Interfaz del asistente (IDTWizard) | Microsoft Docs
description: El IDE usa la interfaz IDTWizard para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para instalarse en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc33d2fb37db7e021ce1752c642492a80956b61f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935942"
---
# <a name="wizard-interface-idtwizard"></a>Interfaz de asistente (IDTWizard)
El entorno de desarrollo integrado (IDE) utiliza la <xref:EnvDTE.IDTWizard> interfaz para comunicarse con los asistentes. Los asistentes deben implementar esta interfaz para poder instalarse en el IDE.

 El <xref:EnvDTE.IDTWizard.Execute%2A> método es el único método asociado a la <xref:EnvDTE.IDTWizard> interfaz. Los asistentes implementan este método y el IDE llama al método en la interfaz. En el ejemplo siguiente se muestra la firma del método.

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

 El mecanismo de inicio es similar para los asistentes **nuevo proyecto** y **Agregar nuevo elemento** . Para iniciar cualquiera de ellos, debe llamar a la <xref:EnvDTE.IDTWizard> interfaz definida en Dteinternal. h. La única diferencia es el conjunto de parámetros personalizados y de contexto que se pasan a la interfaz cuando se llama a la interfaz.

 La siguiente información describe la <xref:EnvDTE.IDTWizard> interfaz que los asistentes deben implementar para trabajar en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. El IDE llama al <xref:EnvDTE.IDTWizard.Execute%2A> método en el asistente y lo pasa a lo siguiente:

- El objeto DTE

     El objeto DTE es la raíz del modelo de automatización.

- Identificador del cuadro de diálogo de la ventana, tal como se muestra en el segmento de código, `hwndOwner ([in] long)` .

     El asistente lo usa `hwndOwner` como elemento primario para el cuadro de diálogo del asistente.

- Parámetros de contexto que se pasan a la interfaz como variante para SAFEARRAY, tal como se muestra en el segmento de código `[in] SAFEARRAY (VARIANT)* ContextParams` .

     Los parámetros de contexto contienen una matriz de valores que son específicos del tipo de asistente que se está iniciando y el estado actual del proyecto. El IDE pasa los parámetros de contexto al asistente. Para obtener más información, vea [parámetros de contexto](../../extensibility/internals/context-parameters.md).

- Los parámetros personalizados que se pasan a la interfaz como una variante de SAFEARRAY, tal como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     Los parámetros personalizados contienen una matriz de parámetros definidos por el usuario. Un archivo. vsz pasa los parámetros personalizados al IDE. Los valores se determinan mediante las `Param=` instrucciones. Para obtener más información, vea [Custom Parameters](../../extensibility/internals/custom-parameters.md).

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
