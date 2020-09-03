---
title: Glosario del depurador de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 954532311fe6b63fc288877a6d41722e6ea47581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713348"
---
# <a name="visual-studio-debugger-glossary"></a>Glosario del depurador de Visual Studio
A continuación se muestran los términos que se usan en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuración.

## <a name="terms"></a>Términos
 punto de interrupción enlazado una abstracción para un punto de interrupción establecido en el código. Hay una relación uno a uno entre un punto de interrupción enlazado y una instrucción de punto de interrupción en la secuencia de código. Cuando se descarga el código, los puntos de interrupción enlazados se pueden Desenlazar.

 la causalidad proporciona la capacidad de realizar un seguimiento de un subproceso lógico de ejecución a través de varios subprocesos físicos, procesos y máquinas, y reconstruir la pila de llamadas de ese subproceso lógico en un momento dado de la duración del subproceso.

 el contexto de código proporciona una abstracción de una posición en el código conocido para el motor de depuración. En el caso de la mayoría de las arquitecturas en tiempo de ejecución, un contexto de código es una dirección de la secuencia de instrucciones de un programa. En el caso de los lenguajes no tradicionales, en los que es posible que el código no se represente mediante instrucciones, un contexto de código puede representarse por otros medios.

 la ruta de acceso del código representa un punto de ejecución en el código donde se realiza una bifurcación o se realiza una llamada de función. Un seguimiento de la pila es esencialmente una lista de rutas de acceso del código de llamada de función.

 motor de depuración (DE) componente que permite la depuración de una arquitectura en tiempo de ejecución. Un motor de depuración funciona junto con el intérprete o el sistema operativo y proporciona servicios de depuración, como el control de ejecución, los puntos de interrupción y la evaluación de expresiones.

 el contexto del documento proporciona una abstracción de una posición en un documento de archivo de código fuente conocido para el motor de depuración. Para la mayoría de los lenguajes, un contexto de documento es una posición en un archivo de código fuente. En el caso de los idiomas no tradicionales, para los que el archivo de origen puede no ser texto, un contexto de documento podría representarse por otros medios. Vea también *posición del documento*.

 la posición del documento proporciona una abstracción de una posición en un archivo de código fuente conocido para el IDE. Para la mayoría de los lenguajes, una posición de documento es una posición en un archivo de código fuente. En el caso de los idiomas no tradicionales, una posición de documento podría representarse de otras formas. Vea también *contexto del documento*.

 error de punto de interrupción una abstracción para describir un error en un punto de interrupción pendiente. Un punto de interrupción de error puede describir un error en la ubicación del punto de interrupción pendiente, la expresión asociada con el punto de interrupción pendiente u otra información que impide que el punto de interrupción pendiente se enlace a una ubicación de código.

 el contexto de evaluación proporciona una abstracción de un contexto de programación para la evaluación de expresiones. Normalmente, un contexto de evaluación es un ámbito. Al realizar la evaluación de expresiones en un contexto de expresión, el contexto de la expresión proporciona reglas de ámbito que coinciden con su punto de creación. Por ejemplo, un contexto de expresión creado en un marco de pila proporcionará el contexto para evaluar las variables locales, los parámetros de método, los miembros de clase (si procede) y las variables globales.

 excepción interceptada excepción que intercepta un motor de depuración, aunque no haya ningún mecanismo de control de excepciones en el marco de pila actual.

 JustMyCode el concepto de depurar solo el código que pertenece a un usuario y omitir todo el código intermedio, como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.

 el punto de interrupción pendiente proporciona una abstracción para los puntos de interrupción antes, durante y después de que se cargue el código y una manera de virtualizar los puntos de interrupción. Un punto de interrupción pendiente:

- Contiene toda la información necesaria para enlazar un punto de interrupción al código en uno o varios programas.

- Puede enlazar a varias ubicaciones de código en uno o varios programas.

- Nunca se enlaza al código.

  Cada vez que se carga el código, se comprueban todos los puntos de interrupción pendientes en un programa para ver si se pueden enlazar. Se dice que un punto de interrupción pendiente contiene todos los puntos de interrupción enlazados que se enlazan.

  procesa un proceso físico de Win32. Un proceso puede contener varios programas. Vea también *programa*.

  Programe un único espacio de nombres que se ejecute dentro de una arquitectura en tiempo de ejecución determinada. Vea también *Process*.

  el administrador de depuración de sesión (SDM) administra cualquier número de motores de depuración que depure cualquier número de programas en varios procesos en cualquier número de equipos. En el nivel básico, el SDM es un multiplexor de motores de depuración. Además, el SDM proporciona una vista unificada de la sesión de depuración en el IDE.

  el marco de pila representa el estado de cálculo en un marco determinado y un nivel determinado de llamadas a funciones anidadas.

  Thread la noción generalizada de la ejecución de instrucciones basadas en la pila que se ejecuta en al menos un programa.

  punto de interrupción de advertencia una abstracción para describir una advertencia en un punto de interrupción pendiente. Un punto de interrupción de advertencia describe el motivo por el que el punto de interrupción pendiente todavía no se ha enlazado a una ubicación de código. Esto puede deberse a que el código aún no se ha cargado para la ubicación descrita por el punto de interrupción pendiente o por algún otro motivo.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
