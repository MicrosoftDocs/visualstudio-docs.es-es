---
title: Administración de una galería privada mediante la configuración del Registro
description: Obtenga información sobre cómo controlar el acceso a los controles, plantillas y herramientas de la galería de Visual Studio, la Galería de ejemplos o las galerías privadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9fef1e6447ac07e9c3d4ccfb76a9ee1e06f91e42
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898840"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Cómo: Administrar una galería privada mediante la configuración del Registro
Si es administrador o desarrollador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas de la galería de Visual Studio, la Galería de ejemplos o las galerías privadas. Para que una galería esté disponible o no disponible, cree un *archivo .pkgdef* que describa las claves del Registro modificadas y sus valores.

## <a name="manage-private-galleries"></a>Administración de galerías privadas
 Puede crear un archivo *.pkgdef para* controlar el acceso a las galerías en varios equipos. Este archivo debe tener el formato siguiente.

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

 La `Repositories` clave hace referencia a la galería que se va a habilitar o deshabilitar. La Visual Studio y la Galería de ejemplos usan los siguientes GUID de repositorio:

- Visual Studio Gallery: 0F45E408-7995-4375-9485-86B8DB553DC9

- Galería de ejemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  El `Disabled` valor es opcional. De forma predeterminada, una galería está habilitada.

  El valor determina el orden en que se enumeran las `Priority` galerías en el **cuadro de diálogo** Opciones. Visual Studio Gallery tiene prioridad 10 y la Galería de ejemplos tiene prioridad 20. Las galerías privadas comienzan en la prioridad 100. Si varias galerías tienen el mismo valor de prioridad, el orden en que aparecen viene determinado por los valores de sus atributos `DisplayName` localizados.

  El valor es necesario para las galerías basadas en Atom o `Protocol` SharePoint.

  Debe `DisplayName` especificarse , `DisplayNameResourceID` o y `DisplayNamePackageGuid` . Si se especifican todos, se usa `DisplayNameResourceID` el `DisplayNamePackageGuid` par y .

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilitar la galería Visual Studio con un archivo .pkgdef
 Puede deshabilitar una galería en un *archivo .pkgdef.* La entrada siguiente deshabilita la galería Visual Studio datos:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 La entrada siguiente deshabilita la Galería de ejemplos:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Consulta también
- [Galerías privadas](../extensibility/private-galleries.md)
