---
title: "Cómo: administrar una galería privada mediante la configuración del registro | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7f9c12cef9b46cc29c4fda6ad74855b69386dc9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Cómo: administrar una galería privada mediante la configuración del registro
Si eres un administrador o el programador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas en la Galería de Visual Studio, la Galería de ejemplos o galerías privadas. Para realizar una galería disponible o no está disponible, cree un archivo .pkgdef que describe las claves del registro modificada y sus valores.  
  
## <a name="managing-private-galleries"></a>Administrar ensamblados privados  
 Puede crear un archivo .pkgdef para controlar el acceso a galerías en varios equipos. Este archivo debe tener el formato siguiente.  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 El `Repositories` clave hace referencia a la Galería para habilitar o deshabilitar. La Galería de Visual Studio y la Galería de ejemplos utilizan el repositorio siguiente GUID:  
  
-   Galería de Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   Galería de ejemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 El `Disabled` valor es opcional. De forma predeterminada, se habilita una galería.  
  
 El `Priority` valor determina el orden en que se muestran las galerías en el cuadro de diálogo de opciones. Galería de Visual Studio tiene prioridad 10 y la Galería de ejemplos tiene prioridad 20. Galerías privadas empiezan en prioridad 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen se determina por los valores de su versión traducida `DisplayName` atributos.  
  
 El `Protocol` valor se requiere para galerías basado en SharePoint o Atom.  
  
 Ya sea `DisplayName`, o ambos `DisplayNameResourceID` y `DisplayNamePackageGuid`, debe especificarse. Si se especifica, la `DisplayNameResourceID` y `DisplayNamePackageGuid` par se utiliza.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilitar la Galería de Visual Studio mediante un archivo .pkgdef  
 Puede deshabilitar una galería en un archivo .pkgdef. La entrada siguiente deshabilita la Galería de Visual Studio:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 La entrada siguiente deshabilita la Galería de ejemplos:  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)