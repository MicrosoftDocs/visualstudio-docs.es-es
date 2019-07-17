---
title: Procedimiento Administrar una galería privada mediante la configuración del registro | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204156"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedimiento Administrar una galería privada mediante la configuración del Registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si es un administrador o el desarrollador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas en la Galería de Visual Studio, la Galería de ejemplos o galerías privadas. Para hacer una galería disponibles o no, cree un archivo .pkgdef que describe las claves del registro modificada y sus valores.  
  
## <a name="managing-private-galleries"></a>Administrar galerías privadas  
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
  
 El `Repositories` clave hace referencia a la Galería para habilitarse o deshabilitarse. La Galería de Visual Studio y la Galería de ejemplos utilizan el repositorio siguiente GUID:  
  
- Galería de Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galería de ejemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  El `Disabled` valor es opcional. De forma predeterminada, una galería está habilitada.  
  
  El `Priority` valor determina el orden en que se enumeran las galerías en el cuadro de diálogo Opciones. Galería de Visual Studio tiene prioridad 10 y la Galería de ejemplos tiene prioridad 20. Galerías privadas se inician en la prioridad de 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen viene determinada por los valores de su versión traducida `DisplayName` atributos.  
  
  El `Protocol` valor es obligatorio para galerías basado en SharePoint o Atom.  
  
  Ya sea `DisplayName`, o ambos `DisplayNameResourceID` y `DisplayNamePackageGuid`, debe especificarse. Si se especifica, la `DisplayNameResourceID` y `DisplayNamePackageGuid` par se utiliza.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilitación de la Galería de Visual Studio mediante un archivo .pkgdef  
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
  
## <a name="see-also"></a>Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)
