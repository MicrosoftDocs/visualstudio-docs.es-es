---
title: Mediante el modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37a5fb96d7f1e63bf28a9227333362ff79f3cd3d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62857500"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
Después de haberse conectado a la automatización de su VSPackage, puede obtener las propiedades y métodos mediante una llamada a la <xref:EnvDTE.DTEClass.GetObject%2A> método en el <xref:EnvDTE._DTE> objeto, pasando una cadena que representa el objeto que desea recuperar.

## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto
 Los siguientes son dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto de objetos de automatización. Para obtener información acerca de cómo obtener el objeto DTE, vea [Cómo: Obtener referencias a los objetos DTE y DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 En este momento, puede usar los objetos de proyecto estándar que forman parte de un VSPackage concreto para bajar el modelo de jerarquía.

 El ejemplo de código siguiente muestra cómo obtener un objeto personalizado que es una propiedad de un tipo de proyecto personalizado.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 El código siguiente enumera los nombres de todas las propiedades en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno **General** opción el **herramientas** menú:

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