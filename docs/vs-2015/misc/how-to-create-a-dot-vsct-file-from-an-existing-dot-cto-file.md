---
title: Procedimiento Crear una. Archivo de Vsct desde una existente. Archivo CTO | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056177"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Procedimiento Crear una. Archivo de Vsct desde una existente. Archivo de director de tecnología
Puede crear un archivo .vsct basado en XML a partir de un archivo .cto binario existente. Si lo hace, podrá aprovechar el nuevo formato de compilador de tabla de comandos. Este proceso funciona aunque el archivo .cto esté compilado a partir de un archivo .ctc. Puede editar y compilar el archivo .vsct en otro archivo .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para crear un archivo .vsct a partir de un archivo .cto  
  
1. Obtenga copias del archivo .cto y el archivo .ctsym correspondiente.  
  
2. Coloque los archivos en el mismo directorio que el compilador vsct.exe.  
  
3. En el símbolo del sistema de Visual Studio, vaya al directorio que contiene los archivos .cto y .ctsym.  
  
4. Escriba **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**.  
  
     `ctofilename` es el nombre del archivo .cto, `vsctfilename` es el nombre del archivo .vsct que desea crear y `symfilename` es el nombre del archivo .ctsym.  
  
     Este proceso crea un nuevo archivo compilador de tabla de comandos XML .vsct. Puede editar y compilar el archivo con vsct.exe, el compilador de .vsct, tal como lo haría con cualquier otro archivo .vsct.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear una. Archivo de Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)