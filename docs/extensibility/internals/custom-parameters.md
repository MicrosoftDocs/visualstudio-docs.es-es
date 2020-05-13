---
title: Parámetros personalizados ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708947"
---
# <a name="custom-parameters"></a>Parámetros personalizados
Los parámetros personalizados controlan el funcionamiento de un asistente después de que se haya iniciado un asistente. Un archivo *.vsz* relacionado proporciona una matriz de parámetros definidos por el usuario empaquetados por el entorno de desarrollo integrado (IDE) y pasados al asistente como una matriz de cadenas cuando se inicia el asistente. A continuación, el asistente analiza la matriz de cadenas y utiliza la información para controlar el funcionamiento real del asistente. De esta manera, un asistente puede personalizar la funcionalidad en función del contenido del archivo *.vsz.*

 Los parámetros de contexto, por otro lado, definen el estado del proyecto cuando se inicia el asistente. Para obtener más información, consulte [Parámetros de contexto](../../extensibility/internals/context-parameters.md).

 A continuación se muestra un ejemplo de un archivo *.vsz* que tiene parámetros personalizados:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 El autor del archivo *.vsz* agrega los valores de los parámetros. Cuando un usuario selecciona **Nuevo proyecto** o Agregar **nuevo elemento** en **el** archivo menú o haciendo clic en un proyecto en el **Explorador**de soluciones , el IDE recopila estos valores en una matriz de cadenas. A continuación, el IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> llama <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> al método del proyecto <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> con el conjunto de indicadores y el proyecto llama al método responsable de ejecutar el asistente y devolver el resultado.

 El asistente es responsable de analizar la matriz de cadenas y actuar en las cadenas de forma adecuada. De esta manera, mediante la implementación de parámetros personalizados puede crear un asistente que realice una variedad de funciones. En otras palabras, un asistente podría tener tres archivos *.vsz* diferentes. Cada archivo pasa diferentes conjuntos de parámetros personalizados para controlar el comportamiento del asistente en varias situaciones.

 Para obtener más información, consulte [Wizard (.vsz) file](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)
- [Asistentes](../../extensibility/internals/wizards.md)
- [Archivo Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
