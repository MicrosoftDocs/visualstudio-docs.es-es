---
title: Comando Shell | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7b3b8d5e2e86dd613d16c1bcec8d6819765eeb8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577833"
---
# <a name="shell-command"></a>Shell (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [comando Shell](https://docs.microsoft.com/visualstudio/ide/reference/shell-command).  
  
  
Inicia programas ejecutables desde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Argumentos  
 `path`  
 Requerido. El nombre de archivo y la ruta de acceso del archivo que se va a ejecutar o el documento que se va a abrir. Se necesita una ruta de acceso completa si el archivo especificado no está en uno de los directorios de la variable de entorno PATH.  
  
 `args`  
 Opcional. Argumentos que se pasan al programa invocado.  
  
## <a name="switches"></a>Modificadores  
 /commandwindow [o] /command [o] /c [o] /cmd  
 Opcional. Especifica que la salida del ejecutable se muestra en la ventana **Comandos**.  
  
 /dir:`folder` [o] /d: `folder`  
 Opcional. Especifica el directorio de trabajo que se establecerá cuando se ejecute el programa.  
  
 /outputwindow [u] /output [u] /out [u] /o  
 Opcional. Especifica que la salida del ejecutable se muestra en la ventana **Salida**.  
  
## <a name="remarks"></a>Comentarios  
 Los modificadores /dir /o /c tienen que especificarse inmediatamente después de `Tools.Shell`. Cualquier elemento especificado después del nombre del ejecutable se pasa como argumentos de línea de comandos.  
  
 El alias predefinido `Shell` se puede usar en lugar de `Tools.Shell`.  
  
> [!CAUTION]
>  Si el argumento `path` proporciona la ruta de acceso de directorio, así como el nombre de archivo, debe incluir la ruta de acceso completa entre comillas literales ("""), como en el siguiente ejemplo:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 El procesador `Shell` interpreta cada conjunto de tres comillas dobles (""") como un único carácter de comilla doble. Por tanto, en el ejemplo anterior, se pasa la siguiente cadena de ruta de acceso al comando `Shell`:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Si no se coloca la cadena de ruta de acceso entre comillas literales ("""), Windows usará solo la parte de la cadena hasta el primer espacio. Por ejemplo, si la cadena de ruta de acceso anterior no se hubiera colocado correctamente entre comillas, Windows buscaría un archivo denominado "Program" que se encuentra en el directorio raíz C:\. Si un archivo ejecutable C:\Program.exe estuviera disponible, incluso uno instalado por una manipulación ilícita, Windows intentaría ejecutar ese programa en lugar del programa "C:\Archivos de programa\SomeFile.exe" deseado.  
  
## <a name="example"></a>Ejemplo  
 El siguiente comando usa xcopy.exe para copiar el archivo `MyText.txt` en la carpeta `Text`. La salida de xcopy.exe se muestra tanto en la **ventana Comandos** como en la ventana de **salida**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Ventana de salida](../../ide/reference/output-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



