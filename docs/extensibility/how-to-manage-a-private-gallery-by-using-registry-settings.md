---
title: 'Cómo: Administrar una galería privada mediante la configuración del registro . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710935"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Cómo: Administrar una galería privada mediante la configuración del Registro
Si es administrador o desarrollador de una extensión de Shell aislado, puede controlar el acceso a los controles, plantillas y herramientas de la Galería de Visual Studio, la Galería de ejemplos o galerías privadas. Para que una galería esté disponible o no esté disponible, cree un archivo *.pkgdef* que describa las claves del Registro modificadas y sus valores.

## <a name="manage-private-galleries"></a>Gestionar galerías privadas
 Puede crear un archivo *.pkgdef* para controlar el acceso a las galerías en varios equipos. Este archivo debe tener el siguiente formato.

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

 La `Repositories` clave hace referencia a la galería que se va a habilitar o deshabilitar. La Galería de Visual Studio y la Galería de ejemplos usan los siguientes GUID de repositorio:

- Galería de Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galería de muestras : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  El `Disabled` valor es opcional. De forma predeterminada, una galería está habilitada.

  El `Priority` valor determina el orden en el que se enumeran las galerías en el cuadro de diálogo **Opciones.** La Galería de Visual Studio tiene la prioridad 10 y la Galería de ejemplos tiene la prioridad 20. Las galerías privadas comienzan en la prioridad 100. Si varias galerías tienen el mismo valor de prioridad, el orden `DisplayName` en el que aparecen viene determinado por los valores de sus atributos localizados.

  El `Protocol` valor es necesario para las galerías basadas en Atom o SharePoint.

  Debe `DisplayName`especificarse `DisplayNameResourceID` `DisplayNamePackageGuid`, o ambos y , . Si se especifican todos, `DisplayNameResourceID` `DisplayNamePackageGuid` se utiliza el par y.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Deshabilite la Galería de Visual Studio mediante un archivo .pkgdef
 Puede deshabilitar una galería en un archivo *.pkgdef.* La entrada siguiente deshabilita la Galería de Visual Studio:

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
