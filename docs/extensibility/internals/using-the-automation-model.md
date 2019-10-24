---
title: Usar el modelo de automatización | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f1e1479232a684758359de7527f0c2fc9990cc7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722091"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
Una vez que haya conectado el VSPackage a Automation, puede obtener las propiedades y los métodos llamando al método <xref:EnvDTE.DTEClass.GetObject%2A> en el objeto <xref:EnvDTE._DTE>, pasando una cadena que representa el objeto que desea recuperar.

## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto
 A continuación se muestran dos ejemplos de código que muestran cómo un consumidor de automatización obtiene los objetos de automatización del proyecto. Para obtener información sobre cómo obtener el objeto DTE, vea [Cómo: obtener referencias a los objetos DTE y DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 En este momento, puede usar los objetos de proyecto estándar que forman parte de un VSPackage específico para bajar el modelo de jerarquía.

 En el ejemplo de código siguiente se muestra cómo obtener un objeto personalizado que es una propiedad de un tipo de proyecto personalizado:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 En el código siguiente se muestran los nombres de todas las propiedades de la opción **General** del entorno de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el menú **herramientas** :

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