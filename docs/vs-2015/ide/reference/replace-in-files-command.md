---
title: Comando Reemplazar en archivos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba6dfcf95c006fb05d4faaa0c370c9dba56e4e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197670"
---
# <a name="replace-in-files-command"></a>Reemplazar en archivos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Reemplaza texto de los archivos mediante el uso de un subconjunto de las opciones disponibles en la pestaña **Reemplazar en archivos** de la ventana **Buscar y reemplazar**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>Argumentos  
 `findwhat`  
 Requerido. Texto que debe coincidir.  
  
 `replacewith`  
 Requerido. Texto que va a sustituir el texto coincidente.  
  
## <a name="switches"></a>Modificadores  
 /all o /a  
 Opcional. Reemplaza todas las apariciones del texto de la búsqueda por el texto de reemplazo.  
  
 /case o /c  
 Opcional. Se encuentran coincidencias solo si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.  
  
 /ext: `extensions`  
 Opcional. Especifica las extensiones de los archivos en los que se va a buscar.  
  
 /keep o /k  
 Opcional. Especifica que todos los archivos modificados se dejan abiertos.  
  
 /lookin: `searchpath`  
 Opcional. Directorio en el que se va a buscar. Si la ruta de acceso contiene espacios, incluya la ruta de acceso completa entre comillas.  
  
 /options o /t  
 Opcional. Muestra una lista de los valores de la opción de búsqueda actual y no lleva a cabo una búsqueda.  
  
 /regex o /r  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan patrones de texto en lugar de los caracteres literales. Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset o /e  
 Opcional. Establece las opciones de búsqueda en su configuración predeterminada y no lleva a cabo una búsqueda.  
  
 /stop  
 Opcional. Detiene la operación de búsqueda actual, si hay alguna en curso. El reemplazo omite el resto de los argumentos cuando se ha especificado `/stop`. Por ejemplo, para detener el reemplazo actual, escriba lo siguiente:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 /sub o /s  
 Opcional. Busca en las subcarpetas dentro del directorio especificado en el argumento /lookin:`searchpath`.  
  
 /text2 o /2  
 Opcional. Muestra los resultados del reemplazo en la ventana **Resultados de la búsqueda 2**.  
  
 /wild o /l  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones para representar un carácter o una secuencia de caracteres.  
  
 /word o /w  
 Opcional. Busca solo palabras completas.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se busca `btnCancel` y se reemplaza por `btnReset` en todos los archivos .cls ubicados en la carpeta "my visual studio projects". Además, se muestra la información de reemplazo en la ventana **Resultados de la búsqueda 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>Vea también  
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)   
 [Reemplazar en archivos](../../ide/replace-in-files.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



