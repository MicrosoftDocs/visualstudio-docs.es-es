---
title: Comando Buscar | Microsoft Docs
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
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf2ef55aa291016719c5f481d70dadd09f4403d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259186"
---
# <a name="find-command"></a>Buscar (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Busca en los archivos mediante el uso de un subconjunto de las opciones disponibles en la pestaña **Buscar en archivos** de la ventana **Buscar y reemplazar**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Argumentos  
 `findwhat`  
 Requerido. Texto que debe coincidir.  
  
## <a name="switches"></a>Modificadores  
 /case o /c  
 Opcional. Se encuentran coincidencias solo si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.  
  
 /doc o /d  
 Opcional. Busca solo en el documento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /markall o /m  
 Opcional. Coloca un gráfico en cada línea que contenga una coincidencia de búsqueda en el documento actual.  
  
 /open o /o  
 Opcional. Busca en todos los documentos abiertos como si fueran un documento. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /options o /t  
 Opcional. Muestra una lista de los valores de la opción de búsqueda actual y no lleva a cabo una búsqueda.  
  
 /proc o /p  
 Opcional. Busca solo en el procedimiento actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /reset o /e  
 Opcional. Establece las opciones de búsqueda en su configuración predeterminada y no lleva a cabo una búsqueda.  
  
 /sel o /s  
 Opcional. Busca solo en la selección actual. Especifique solo uno de los ámbitos de búsqueda disponibles: `/doc`, `/proc`, `/open` o `/sel`.  
  
 /up o /u  
 Opcional. Busca desde la ubicación actual en el archivo hacia el principio del archivo. De forma predeterminada, las búsquedas comienzan en la ubicación actual en el archivo y buscan hacia el final del archivo.  
  
 /regex o /r  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan patrones de texto en lugar de los caracteres literales. Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /wild o /l  
 Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones para representar un carácter o una secuencia de caracteres.  
  
 /word o /w  
 Opcional. Busca solo palabras completas.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se realiza una búsqueda que distingue entre mayúsculas y minúsculas de la palabra "somestring" en la sección de código seleccionada.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Vea también  
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



