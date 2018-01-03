---
title: Comando ShowWebBrowser | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="showwebbrowser-command"></a>ShowWebBrowser (Comando)
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
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)