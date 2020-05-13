---
title: Uso del modelo de automatización ( Automation Model) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704220"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
Después de conectar el VSPackage a la automatización, <xref:EnvDTE.DTEClass.GetObject%2A> puede obtener <xref:EnvDTE._DTE> las propiedades y métodos mediante una llamada al método en el objeto, pasando una cadena que representa el objeto que desea recuperar.

## <a name="obtaining-project-objects"></a>Obtención de objetos de proyecto
 Los siguientes son dos ejemplos de código que muestran cómo un consumidor de automatización obtiene los objetos de automatización del proyecto. Para obtener información sobre cómo obtener el objeto DTE, consulte [Cómo: Obtener referencias a los objetos DTE y DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 En este punto, puede usar los objetos de proyecto estándar que forman parte de un VSPackage específico para desplazarse por el modelo de jerarquía.

 En el ejemplo de código siguiente se muestra cómo obtener un objeto personalizado que es una propiedad de un tipo de proyecto personalizado.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 El código siguiente enumera los nombres de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] todas las propiedades en el entorno **General** opción en el **herramientas** menú:

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Vea también
- <xref:EnvDTE.DTEClass.GetObject%2A>
