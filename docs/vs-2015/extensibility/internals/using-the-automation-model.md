---
title: Mediante el modelo de automatización | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea911dd70ae3a5ca0e53888b47ed2a8d859827c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789140"
---
# <a name="using-the-automation-model"></a>Uso del modelo de automatización
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Después de haberse conectado a la automatización de su VSPackage, puede obtener las propiedades y métodos mediante una llamada a la <xref:EnvDTE.DTEClass.GetObject%2A> método en el <xref:EnvDTE._DTE> objeto, pasando una cadena que representa el objeto que desea recuperar.  
  
## <a name="obtaining-project-objects"></a>Obtener objetos de proyecto  
 Los siguientes son dos ejemplos de código que muestran cómo un consumidor de automatización Obtiene el proyecto de objetos de automatización. Para obtener información acerca de cómo obtener el objeto DTE, vea [Cómo: obtener referencias a los objetos DTE y DTE2](http://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 El código siguiente enumera los nombres de todas las propiedades en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno **General** opción el **herramientas** menú:  
  
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

