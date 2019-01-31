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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c1fca2c1c1dde167c8028d6ad4d543e108a488b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798218"
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Muestra la dirección URL especificada en una ventana del explorador web dentro o fuera del entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 En el ejemplo siguiente se muestra la página principal de MSDN Online en un explorador web fuera del IDE. Si una instancia del explorador web ya está abierta, se usa; en caso contrario, se inicia una nueva instancia.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
