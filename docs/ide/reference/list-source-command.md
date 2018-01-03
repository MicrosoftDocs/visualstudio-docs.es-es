---
title: "Mostrar código fuente (Comando) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bb3f3e6cb441697fb8546fcec485d292e979690b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="list-source-command"></a>Mostrar código fuente (Comando)
Muestra las líneas de código fuente especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Modificadores  
 /Count:`number`  
 Opcional. Especifica el número de líneas que se van a mostrar.  
  
 /Current  
 Opcional. Muestra la línea actual.  
  
 /File:`filename`  
 Opcional. Ruta de acceso del archivo que se va a mostrar. Si no se especifica ningún nombre de archivo, el comando muestra el código fuente para la línea de la instrucción actual.  
  
 /Line:`number`  
 Opcional. Muestra un número de línea concreto.  
  
 /ShowLineNumbers:`yes|no`  
 Opcional. Especifica si se mostrarán o no los números de línea.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra el código fuente desde la línea 4 del archivo Form1.vb, con los números de línea visibles.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)