---
title: Comando ShowWebBrowser | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663518"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra la dirección URL especificada en una ventana del explorador web dentro o fuera del entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argumentos
 `URL` Obligatorio. Dirección URL (localizador uniforme de recursos) del sitio web.

## <a name="switches"></a>Modificadores
 /New opcional. Especifica que la página aparece en una nueva instancia del explorador web.

 /ext opcional. Especifica que la página aparece en el explorador web predeterminado fuera del IDE.

## <a name="remarks"></a>Observaciones
 El alias del comando **ShowWebBrowser** es **navigate** o **nav**.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra la página principal de MSDN Online en un explorador web fuera del IDE. Si una instancia del explorador web ya está abierta, se usa; en caso contrario, se inicia una nueva instancia.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
