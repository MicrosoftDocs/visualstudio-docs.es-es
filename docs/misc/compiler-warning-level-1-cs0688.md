---
title: "Advertencia del compilador (nivel 1) CS0688 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0688"
ms.assetid: 8ce5af36-663e-46e8-87e9-bb32555796ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0688
'método' tiene una petición de vínculo, pero reemplaza o implementa 'método2' que no tiene una petición de vínculo. Puede existir una vulnerabilidad de seguridad.  
  
 La petición de vínculo configurada en el método de clase derivada puede evitarse fácilmente llamando al método de clase base. Para solucionar la vulnerabilidad de seguridad, el método de clase base debe usar también la petición de vínculo. Para obtener más información, vea [Demand frente a LinkDemand](http://msdn.microsoft.com/es-es/1ab877f2-70f4-4e0d-8116-943999dfe8f5).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0688. Para resolver la advertencia sin modificar la clase base, quite el atributo de seguridad del método de reemplazo. No solucionará el problema de seguridad.  
  
```  
// CS0688.cs // compile with: /W:1 using System; using System.Security.Permissions; class Base { //Uncomment the following line to close the security hole //[FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] public virtual void DoScaryFileStuff() { } } class Derived: Base { [FileIOPermission(SecurityAction.LinkDemand, All=@"C:\\")] // CS0688 public override void DoScaryFileStuff() { } static void Main() { } }  
```