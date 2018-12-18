---
title: Comando Replace | Microsoft Docs
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
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83281a656d553dfa677d7ae25bf043fc0b588978
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283210"
---
# <a name="replace-command"></a>Reemplazar (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Reemplaza texto de los archivos mediante el uso de un subconjunto de las opciones disponibles en la pestaña **Reemplazar en archivos** de la ventana **Buscar y reemplazar**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
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
  
 /doc o /d  
 Opcional. Busca solo en el documento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /hidden o /h  
 Opcional. Busca texto oculto y contraído, como los metadatos de un control en tiempo de diseño, una región oculta de un documento de esquema o una clase o método contraídos.  
  
 /open o /o  
 Opcional. Busca en todos los documentos abiertos como si fueran un documento. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /options o /t  
 Opcional. Muestra una lista de los valores de la opción de búsqueda actual y no lleva a cabo una búsqueda.  
  
 /proc o /p  
 Opcional. Busca solo en el procedimiento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /regex o /r  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan patrones de texto en lugar de los caracteres literales. Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset o /e  
 Opcional. Establece las opciones de búsqueda en su configuración predeterminada y no lleva a cabo una búsqueda.  
  
 /sel o /s  
 Opcional. Busca solo en la selección actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /up o /u  
 Opcional. Busca desde la ubicación actual en el archivo hacia la parte superior del archivo. De forma predeterminada, las búsquedas comienzan en la ubicación actual en el archivo y avanzan hacia la parte inferior del archivo.  
  
 /wild o /l  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones para representar un carácter o una secuencia de caracteres.  
  
 /word o /w  
 Opcional. Busca solo palabras completas.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se reemplaza `btnSend` por `btnSubmit` en todos los documentos abiertos.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## <a name="see-also"></a>Vea también  
 [Buscar y reemplazar texto](../../ide/finding-and-replacing-text.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



