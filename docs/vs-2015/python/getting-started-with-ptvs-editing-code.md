---
title: 'Introducción a PTVS: editar código | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: ef0a84523a2d828e696fb50f641f392ab7bbd39f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265790"
---
# <a name="getting-started-with-ptvs-editing-code"></a>Introducción a PTVS: Editar código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS proporciona una productiva experiencia del editor de Visual Studio para Python.  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
 Comience con la plantilla básica de proyecto vacío de aplicación de Python.  
  
 Comience a escribir una línea `from … import` en el editor.  Verá que la lista de finalización emergente enumera todos los módulos que están disponibles para la importación.  Esta lista varía en función de la versión de Python y de las bibliotecas que instaló.  Utilice la biblioteca matemática como ejemplo.  Observará que, a medida que escribe, la lista de finalización filtra los elementos que incluyen los caracteres que escribió.  Complete la instrucción importando el identificador `sin`.  
  
```python  
from math import sin  
  
```  
  
 Durante la codificación, si usa un identificador que no está enlazado pero que puede encontrarse en las bibliotecas, PTVS ofrece una solución rápida emergente para agregar la instrucción de importación adecuada que necesita.  Por ejemplo, si lo hubiera escrito `cos`, a continuación, vería **importar de matemáticas** que ofrece.  
  
 Puede usar un fragmento de código para generar código.  En el menú Edición, elija IntelliSense y, a continuación, Insertar fragmento de código.  Después elija Python y def.  Llame a la función `make_dot_string` y agregue un parámetro `x`.  Puede agregar aserciones en el archivo en este momento para el desarrollo controlado por pruebas, y verá que PTVS ya ofrece la nueva función en las listas de finalización.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 A continuación, vuelva a la función nueva y empiece a escribir el cuerpo siguiente:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 Verá que PTVS supone que el parámetro es un entero, ya que PTVS analizó los sitios de llamada a esta función.   También tendrá que usar la corrección rápida para importar `radians`.  
  
 Use otro fragmento de código para crear un bloque principal. Para ello, escriba `main` en el nivel superior, invoque la interfaz de usuario de la etiqueta inteligente y use la pestaña para elegir «def. principal...».  Escriba un bucle básico para llamar a `make_dot_string`.  Verá que PTVS sabe que la función devuelve una cadena si presiona punto y ve las finalizaciones ofrecidas.  Esta información de tipo fluirá por todo el programa, por lo que podemos proporcionar información sobre herramientas y finalizaciones dondequiera que acaben los valores, de modo que pueda entender y escribir mejor el código.  
  
 Si agrega una llamada a imprimir, tendrá un principal similar al siguiente:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 Si presiona F5, el código se ejecuta en una ventana cmd.exe y verá un punto que oscila atrás y adelante.  
  
 Puede ver estas instrucciones en un breve [vídeo de YouTube](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff).  
  
## <a name="see-also"></a>Vea también  
 [Documentación de la wiki](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [Introducción y vídeos Deep Dive de PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

