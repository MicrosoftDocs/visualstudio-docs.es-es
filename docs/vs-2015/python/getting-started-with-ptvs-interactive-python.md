---
title: 'Introducción a PTVS: Python interactivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780991"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>Introducción a PTVS: Python interactivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las solicitudes interactivas o los bucles de leer-evaluar-imprimir (REPL) son una herramienta clave para los lenguajes de programación productivos.  Permiten ejecutar fragmentos de código para detectar y obtener API, experimentar con el uso de API y desarrollar código de trabajo interactivamente para incluirlo en proyectos o programas.  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 En la ventana Entornos de Python, verá una lista de todos los entornos de Python.  Puede seleccionar cualquiera de ellos para abrir una ventana interactiva o REPL.  Si alguna vez ejecutó Python.exe en un símbolo del sistema, ya estará familiarizado con un REPL de Python.  El REPL le pedirá confirmación, y puede escribir código, presione ENTRAR y ver inmediatamente los resultados del código.  Se trata de un contexto de ejecución activo que incluye todos los estados de las ejecuciones, las asignaciones de variables, etc.  Puede hacer referencia a las variables que contienen resultados en envíos posteriores a la confirmación de REPL.  Puede escribir varias líneas de código y ejecutarlas a la vez (por ejemplo, una declaración de método o varias instrucciones).  
  
 Cuando empiece a usar una biblioteca nueva, REPL es una manera excelente de probarla.  Puede importar la biblioteca, inspeccionar los subpaquetes, clases y funciones.  Python puede indicarle toda de esta información a través de la función `help()`.  Además, Python Tools para Visual Studio (PTVS) proporciona sugerencias y documentación en función del modelo de código que se usa en el editor, lo que hace sin necesidad de ejecutar la biblioteca.  Cuando ejecute el código, PTVS usará información del tiempo de ejecución de Python para mejorar las sugerencias de PTVS.  
  
 La ventana interactiva también resulta útil para el desarrollo de código iterativo o evolutivo, incluido probar el código a medida que se desarrolla.  Puede seleccionar una función en una ventana del editor, presionar el botón derecho del puntero y hacer clic en Enviar a interactiva.  Este comando copia la selección en la ventana interactiva como la entrada siguiente y la ejecuta.  Verá inmediatamente los resultados.  Si necesita realizar cambios en la entrada anterior, puede presionar la flecha arriba para obtener el código, modificarlo y presionar Ctrl+ENTRAR para ejecutar el código.  Si presiona ENTRAR al final de la entrada la ejecuta, pero si presiona ENTRAR en el medio de la entrada inserta una nueva línea.  
  
 Puede abrir una ventana interactiva para cada instalación de Python, tantas como desee.  Hay botones en la parte superior de la ventana para borrar la pantalla, restablecer el contexto de ejecución, etc.  El historial permanecerá intacto.  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Vea también  
 [Documentación de la wiki](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [Introducción y vídeos Deep Dive de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
