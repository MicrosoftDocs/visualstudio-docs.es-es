---
title: Parámetros personalizados | Microsoft Docs
description: Obtenga información sobre cómo crear parámetros personalizados que controlen el funcionamiento de un asistente después de que se haya iniciado un asistente; para ello, modifique un archivo. vsz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1b4927e63bec93fbe7b6730e131a0893372aa70d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902967"
---
# <a name="custom-parameters"></a>Parámetros personalizados
Los parámetros personalizados controlan el funcionamiento de un asistente después de que se haya iniciado un asistente. Un archivo *. vsz* relacionado proporciona una matriz de parámetros definidos por el usuario que se empaquetan en el entorno de desarrollo integrado (IDE) y se pasan al asistente como una matriz de cadenas cuando se inicia el asistente. A continuación, el asistente analiza la matriz de cadenas y usa la información para controlar la operación real del asistente. De esta manera, un asistente puede personalizar la funcionalidad en función del contenido del archivo *. vsz* .

 Los parámetros de contexto, por otro lado, definen el estado del proyecto cuando se inicia el asistente. Para obtener más información, vea [parámetros de contexto](../../extensibility/internals/context-parameters.md).

 A continuación se ofrece un ejemplo de un archivo *. vsz* con parámetros personalizados:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 El autor del archivo *. vsz* agrega los valores de los parámetros. Cuando un usuario selecciona **nuevo proyecto** o **Agregar nuevo elemento** en el menú **archivo** o haciendo clic con el botón secundario en un proyecto de **Explorador de soluciones**, el IDE recopila estos valores en una matriz de cadenas. A continuación, el IDE llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método del proyecto con la <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> marca establecida y el proyecto llama al <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> método que es responsable de ejecutar el asistente y devolver el resultado.

 El asistente es responsable de analizar la matriz de cadenas y actuar en las cadenas de manera adecuada. De esta manera, al implementar parámetros personalizados, puede crear un asistente que realice una serie de funciones. En otras palabras, un asistente podría tener tres archivos *. vsz* distintos. Cada archivo pasa diferentes conjuntos de parámetros personalizados para controlar el comportamiento del asistente en varias situaciones.

 Para obtener más información, consulte [archivo de asistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo del asistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
