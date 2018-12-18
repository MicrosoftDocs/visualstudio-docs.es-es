---
title: Mediante el modelo de automatización | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6633aefe783cf163ee27f8a0c4a879aec898d325
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495445"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
Después de haberse conectado a la automatización de su VSPackage, puede obtener las propiedades y métodos mediante una llamada a la <xref:EnvDTE.DTEClass.GetObject%2A> método en el <xref:EnvDTE._DTE> objeto, pasando una cadena que representa el objeto que desea recuperar.  
  
## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto  
 Los siguientes son dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto de objetos de automatización. Para obtener información acerca de cómo obtener el objeto DTE, vea [Cómo: obtener referencias a los objetos DTE y DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
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
 <xref:EnvDTE.DTEClass.GetObject%2A>