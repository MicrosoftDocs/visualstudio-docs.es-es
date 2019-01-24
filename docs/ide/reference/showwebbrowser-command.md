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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df5983b0cbc33abe0f5919a93af1450394134a99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985832"
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