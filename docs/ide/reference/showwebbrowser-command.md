---
title: ShowWebBrowser (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a46f37f93340226c669df5db59745af17c7b2464
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958893"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser (Comando)

Muestra la dirección URL especificada en una ventana del explorador web dentro o fuera del entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumentos
 `URL`

 Obligatorio. Dirección URL (localizador uniforme de recursos) del sitio web.

## <a name="switches"></a>Modificadores
 /new

 Opcional. Especifica que la página aparece en una nueva instancia del explorador web.

 /ext

 Opcional. Especifica que la página aparece en el explorador web predeterminado fuera del IDE.

## <a name="remarks"></a>Comentarios
 El alias del comando **ShowWebBrowser** es **navigate** o **nav**.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra la página principal de Microsoft Docs en un explorador web fuera del IDE. Si una instancia del explorador web ya está abierta, se usa; en caso contrario, se inicia una nueva instancia.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)