---
title: Glosario del depurador de Visual Studio | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19d82f006bb1c37981f60e1a0b2710588eb0053c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204781"
---
# <a name="visual-studio-debugger-glossary"></a>Glosario del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Los siguientes son los términos usados en el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK de depuración.  
  
## <a name="terms"></a>Términos  
 punto de interrupción enlazado  
 Una abstracción para un punto de interrupción establecido en el código. Hay una relación uno a uno entre un punto de interrupción enlazado y una instrucción de punto de interrupción en la secuencia de código. Cuando el código descarga, pueden separar los puntos de interrupción enlazados.  
  
 causalidad  
 Proporciona la capacidad para realizar el seguimiento de un subproceso lógico de ejecución a través de varios equipos, procesos y subprocesos físicos y para reconstruir la pila de llamadas del subproceso lógico en un momento determinado de duración del subproceso.  
  
 contexto de código  
 Proporciona una abstracción de una posición en el código que se sabe que el motor de depuración. Para la mayoría de las arquitecturas de tiempo de ejecución, un contexto de código es una dirección en la secuencia de instrucciones de un programa. Para los idiomas no tradicionales, en el que no se puede representar código por instrucciones, se puede representar un contexto de código por otros medios.  
  
 ruta de acceso del código  
 Representa un punto de ejecución en el código donde se toma una rama o se realiza una llamada de función. Un seguimiento de pila es básicamente una lista de rutas de acceso del código de llamada de función.  
  
 motor de depuración (DE)  
 Un componente que permite la depuración de una arquitectura en tiempo de ejecución. Un motor de depuración funciona junto con el sistema operativo o un intérprete y proporciona servicios de depuración, como la evaluación de expresión, los puntos de interrupción y control de ejecución.  
  
 contexto de documento  
 Proporciona una abstracción de una posición en un documento de archivo de origen conocido para el motor de depuración. Para la mayoría de los idiomas, un contexto de documento es una posición en un archivo de origen. Para los idiomas no tradicionales, para que el archivo de origen no puede ser texto, un contexto de documento puede estar representado por otros medios. Vea también *documentar posición*.  
  
 Posición del documento  
 Proporciona una abstracción de una posición en un archivo de origen que se sabe que el IDE. Para la mayoría de lenguajes, una posición de documento es una posición en un archivo de origen. Para los idiomas no tradicionales, una posición de documento puede estar representada de otras maneras. Vea también *contexto de documento*.  
  
 punto de interrupción de error  
 Una abstracción para describir un error en un punto de interrupción pendiente. Un punto de interrupción de error puede describir un error en la ubicación del punto de interrupción pendiente, la expresión asociada con el punto de interrupción pendiente u otra información que impide que el punto de interrupción pendiente de enlace a una ubicación del código.  
  
 Contexto de evaluación  
 Proporciona una abstracción de un contexto de programación para la evaluación de expresión. Normalmente, un contexto de evaluación es un ámbito. Cuando se realiza la evaluación de expresiones en un contexto de expresión, el contexto de expresión proporciona reglas de ámbito que coinciden con su punto de creación. Por ejemplo, el contexto de una expresión que creó en un marco de pila proporcionará el contexto para evaluar las variables locales, parámetros de método, los miembros de clase (si procede) y variables globales.  
  
 excepción interceptada  
 Excepción que se intercepta por un motor de depuración, incluso si ningún mecanismo de control de excepciones está vigente en el marco de pila actual.  
  
 JustMyCode  
 El concepto de depuración solo el código que pertenece a un usuario y se omite todo el código intermedio, como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.  
  
 punto de interrupción pendiente  
 Proporciona una abstracción para los puntos de interrupción antes, durante y después de código está cargado y una forma de virtualizar los puntos de interrupción. Un punto de interrupción:  
  
- Contiene toda la información necesaria para enlazar un punto de interrupción al código en uno o más programas.  
  
- Puede enlazar a varias ubicaciones del código en uno o más programas.  
  
- Nunca se enlaza propio al código.  
  
  Cada código en tiempo de carga, se comprueban todos los puntos de interrupción pendientes en un programa para ver si puede enlazar. Se dice que un punto de interrupción pendiente para que contenga todos los puntos de interrupción enlazados que enlaza.  
  
  proceso  
  Un proceso Win32 físico. Un proceso puede contener varios programas. Vea también *programa*.  
  
  programa  
  Un espacio de nombres único que se ejecuta dentro de una determinada arquitectura de tiempo de ejecución. Vea también *proceso*.  
  
  Administrador de depuración de la sesión (SDM)  
  Administra cualquier número de motores de depuración, depuración de cualquier número de programas en varios procesos en cualquier número de máquinas. En el nivel básico, el SDM es un multiplexor de motores de depuración. Además, el SDM proporciona una vista unificada de la sesión de depuración para el IDE.  
  
  marco de pila  
  Representa el estado del cálculo en un fotograma determinado y un nivel concreto de llamadas a funciones anidadas.  
  
  thread  
  La noción generalizada de ejecución de instrucciones basada en la pila que se ejecuta en al menos un programa.  
  
  punto de interrupción de advertencia  
  Una abstracción para describir una advertencia en un punto de interrupción pendiente. Un punto de interrupción de advertencia describe un motivo por qué el punto de interrupción pendiente no ha enlazado a una ubicación del código. Esto puede ser que el código no ha cargado aún para la ubicación que se describe en el punto de interrupción pendiente, o por algún otro motivo.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
