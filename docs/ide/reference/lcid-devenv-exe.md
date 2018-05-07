---
title: -LCID (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c67b1b7d581a7e4b9d4309bfe432bf2a3298e4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Establece el idioma predeterminado que se usa para texto, moneda y otros valores en el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Argumentos
 `LocaleID` Obligatorio. LCID (identificador de configuración regional) del idioma especificado.

## <a name="remarks"></a>Comentarios
 Carga el IDE y establece el idioma natural predeterminado para el entorno. Este cambio se conserva entre sesiones y se refleja en el panel **Configuración internacional** de las opciones de **Entorno** en el cuadro de diálogo **Opciones** del IDE.

 Si el idioma especificado no está disponible en el sistema del usuario, se omite el modificador /LCID.

 En la tabla siguiente se indican los LCID de los idiomas que admite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

|Lenguaje|LCID|
|--------------|----------|
|Chino (simplificado)|2052|
|Chino (tradicional)|1028|
|Inglés|3082|
|Francés|1036|
|Alemán|1031|
|Italiano|1040|
|Japonés|1041|
|Coreano|1042|
|Español|3082|

## <a name="example"></a>Ejemplo
 En este ejemplo se carga el IDE con cadenas de recursos en inglés.

```
devenv /LCID 1033
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Configuración internacional, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)