---
title: Comando Registrar resultados de la ventana Comandos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 21450a0478bb7f2388cdde6b69f6fe661e9a055c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="log-command-window-output-command"></a>Registrar resultados de la ventana de comandos (Comando)
Copia en un archivo todas las entradas y salidas de la ventana **Comandos**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Argumentos  
 `filename`  
 Opcional. Nombre del archivo de registro. De forma predeterminada, el archivo se crea en la carpeta de perfil del usuario. Si ya existe el nombre de archivo, el registro se anexa al final del archivo existente. Si no se especifica ningún archivo, se usa el último archivo especificado. Si no existe ningún archivo anterior, se crea un archivo de registro predeterminado, denominado cmdline.log.  
  
> [!TIP]
>  Para cambiar la ubicación en la que se guarda el archivo de registro, escriba la ruta de acceso completa del archivo, entre comillas si la ruta de acceso contiene algún espacio.  
  
## <a name="switches"></a>Modificadores  
 /on  
 Opcional. Inicia el registro de la ventana **Comandos** en el archivo especificado y anexa el archivo con la nueva información.  
  
 /off  
 Opcional. Detiene el registro de la ventana **Comandos**.  
  
 /overwrite  
 Opcional. Si el archivo especificado en el argumento `filename` coincide con un archivo existente, se sobrescribe.  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún archivo, se crea el archivo cmdline.log de forma predeterminada. De manera predeterminada, el alias de este comando es Log.  
  
## <a name="examples"></a>Ejemplos  
 Este ejemplo crea un archivo de registro, cmdlog, e inicia el registro de comandos.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Este ejemplo detiene el registro de comandos.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Este ejemplo reanuda el registro de comandos en el archivo de registro usado anteriormente.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)