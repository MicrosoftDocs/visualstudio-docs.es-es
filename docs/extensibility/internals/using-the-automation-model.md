---
title: Usar el modelo de automatización | Microsoft Docs
description: Obtenga información acerca de cómo obtener las propiedades y los métodos de su VSPackage después de conectarse al modelo de automatización.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a25936e0be16231bbe315a2bd29a0d495115f392
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085811"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
Una vez que haya conectado el VSPackage a Automation, puede obtener las propiedades y los métodos llamando al <xref:EnvDTE.DTEClass.GetObject%2A> método en el <xref:EnvDTE._DTE> objeto, pasando una cadena que representa el objeto que desea recuperar.

## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto
 A continuación se muestran dos ejemplos de código que muestran cómo un consumidor de automatización obtiene los objetos de automatización del proyecto. Para obtener información sobre cómo obtener el objeto DTE, vea [Cómo: obtener referencias a los objetos DTE y DTE2](/previous-versions/68shb4dw(v=vs.140)).

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

 En el código siguiente se muestran los nombres de todas las propiedades de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] opción **General** del entorno en el menú **herramientas** :

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Consulte también
- <xref:EnvDTE.DTEClass.GetObject%2A>