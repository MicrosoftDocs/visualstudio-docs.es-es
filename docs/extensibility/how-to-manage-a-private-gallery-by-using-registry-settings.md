---
title: "C&#243;mo: administrar una galer&#237;a privada mediante la configuraci&#243;n del registro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Galerías privadas VSIX, administrar"
  - "Administrar galerías privadas de VSIX"
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo: administrar una galer&#237;a privada mediante la configuraci&#243;n del registro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si es un administrador o el programador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas de la Galería de Visual Studio, la Galería de ejemplos o galerías privadas. Para hacer una galería disponibles o no, cree un archivo .pkgdef que describe las claves del registro modificado y sus valores.  
  
## Administrar galerías privadas  
 Puede crear un archivo .pkgdef para controlar el acceso a las galerías en varios equipos. Este archivo debe tener el formato siguiente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 El `Repositories` clave hace referencia a la Galería para habilitar o deshabilitar. La Galería de Visual Studio y la Galería de ejemplos utilizan el repositorio siguiente GUID:  
  
-   Galería de Visual Studio: 0F45E408\-7995\-4375\-9485\-86B8DB553DC9  
  
-   Galería de ejemplos: AEB9CB40\-D8E6\-4615\-B52C\-27E307F8506C  
  
 El `Disabled` valor es opcional. De forma predeterminada, se habilita una galería.  
  
 El `Priority` valor determina el orden en que se enumeran las galerías en el cuadro de diálogo Opciones. Galería de Visual Studio tiene prioridad 10 y la Galería de ejemplos tiene prioridad 20. Las galerías privadas se inician en prioridad de 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen depende de los valores de sus localizadas `DisplayName` atributos.  
  
 El `Protocol` valor se requiere para galerías basado en SharePoint o Atom.  
  
 Ya sea `DisplayName`, o ambos `DisplayNameResourceID` y `DisplayNamePackageGuid`, debe especificarse. Si se especifica, la `DisplayNameResourceID` y `DisplayNamePackageGuid` se usa par.  
  
## Deshabilitación de la Galería de Visual Studio con un archivo .pkgdef  
 Puede deshabilitar una galería en un archivo .pkgdef. La entrada siguiente deshabilita la Galería de Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La entrada siguiente deshabilita la Galería de ejemplos:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)