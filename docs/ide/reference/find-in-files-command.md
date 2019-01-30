---
title: Buscar en archivos (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03dc4a1c83b3056e4991da6cecbe6c3b7b97324e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958425"
---
# <a name="find-in-files-command"></a>Buscar en archivos (Comando)
Busca en los archivos mediante el uso de un subconjunto de las opciones disponibles en la pestaña **Buscar en archivos** de la ventana **Buscar y reemplazar**.

## <a name="syntax"></a>Sintaxis

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumentos
 `findwhat` Obligatorio. Texto que debe coincidir.

## <a name="switches"></a>Modificadores
 /case o /c Opcional. Se encuentran coincidencias solo si los caracteres en mayúsculas y minúsculas coinciden exactamente con los especificados en el argumento `findwhat`.

 /ext: `extensions` Opcional. Especifica las extensiones de los archivos en los que se va a buscar. Si no se especifica, se usa la extensión anterior, en caso de que se haya indicado una previamente.

 /lookin: `searchpath` Opcional. Directorio en el que se va a buscar. Si la ruta de acceso contiene espacios, incluya la ruta de acceso completa entre comillas.

 /names o /n Opcional. Muestra una lista de nombres de archivo que contienen coincidencias.

 /options o /t Opcional. Muestra una lista de los valores de la opción de búsqueda actual y no lleva a cabo una búsqueda.

 /regex o /r Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones que representan patrones de texto en lugar de los caracteres literales. Para obtener una lista completa de caracteres de expresiones regulares, vea [Expresiones regulares](../../ide/using-regular-expressions-in-visual-studio.md).

 /reset o /e Opcional. Establece las opciones de búsqueda en su configuración predeterminada y no lleva a cabo una búsqueda.

 /stop Opcional. Detiene la operación de búsqueda actual, si hay alguna en curso. La búsqueda omite el resto de los argumentos cuando se ha especificado `/stop`. Por ejemplo, para detener la búsqueda actual, escriba lo siguiente:

```cmd
>Edit.FindinFiles /stop
```

 /sub o /s Opcional. Busca en las subcarpetas dentro del directorio especificado en el argumento /lookin:`searchpath`.

 /text2 o /2 Opcional. Muestra los resultados de la búsqueda en la ventana Resultados de la búsqueda 2.

 /wild o /l Opcional. Usa caracteres especiales predefinidos en el argumento `findwhat` como notaciones para representar un carácter o una secuencia de caracteres.

 /word o /w Opcional. Busca solo palabras completas.

## <a name="example"></a>Ejemplo
 En este ejemplo se busca btnCancel en todos los archivos .cls ubicados en la carpeta "My Visual Studio Projects". Además, se muestra la información de coincidencia en la ventana Resultados de la búsqueda 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Vea también

- [Buscar en archivos](../../ide/find-in-files.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)