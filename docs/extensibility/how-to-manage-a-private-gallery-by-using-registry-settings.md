---
title: Procedimiento Administrar una galería privada mediante la configuración del registro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b4f33f7ecf974fe527f814b9febdc861101f1ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318499"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedimiento Administrar una galería privada mediante la configuración del registro
Si es un administrador o el desarrollador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas en la Galería de Visual Studio, la Galería de ejemplos o galerías privadas. Para realizar una galería disponible o no está disponible, crearía un *.pkgdef* archivo que describe las claves del registro modificada y sus valores.

## <a name="manage-private-galleries"></a>Administrar galerías privadas
 Puede crear un *.pkgdef* archivo para controlar el acceso a las galerías en varios equipos. Este archivo debe tener el formato siguiente.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 El `Repositories` clave hace referencia a la Galería para habilitarse o deshabilitarse. La Galería de Visual Studio y la Galería de ejemplos utilizan el repositorio siguiente GUID:

- Galería de Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Galería de ejemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  El `Disabled` valor es opcional. De forma predeterminada, una galería está habilitada.

  El `Priority` valor determina el orden en que se enumeran las galerías en la **opciones** cuadro de diálogo. Galería de Visual Studio tiene prioridad 10 y la Galería de ejemplos tiene prioridad 20. Galerías privadas se inician en la prioridad de 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen viene determinada por los valores de su versión traducida `DisplayName` atributos.

  El `Protocol` valor es obligatorio para galerías basado en SharePoint o Atom.

  Ya sea `DisplayName`, o ambos `DisplayNameResourceID` y `DisplayNamePackageGuid`, debe especificarse. Si se especifica, la `DisplayNameResourceID` y `DisplayNamePackageGuid` par se utiliza.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilitar la Galería de Visual Studio mediante un archivo .pkgdef
 Puede deshabilitar una galería en una *.pkgdef* archivo. La entrada siguiente deshabilita la Galería de Visual Studio:

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
- [Galerías privadas](../extensibility/private-galleries.md)