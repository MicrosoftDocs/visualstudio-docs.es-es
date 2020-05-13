---
title: Glosario del depurador de Visual Studio (Visual Studio Debugger Glossary) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713348"
---
# <a name="visual-studio-debugger-glossary"></a>Glosario del depurador de Visual Studio
Los siguientes son términos utilizados en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuración.

## <a name="terms"></a>Términos
 punto de interrupción enlazado Una abstracción para un punto de interrupción establecido en el código. Hay una relación uno a uno entre un punto de interrupción enlazado y una instrucción de punto de interrupción en la secuencia de código. Cuando se descarga código, los puntos de interrupción enlazados pueden desvincularse.

 causalidad Proporciona la capacidad de realizar un seguimiento de un subproceso lógico de ejecución en varios subprocesos físicos, procesos y máquinas, y para reconstruir la pila de llamadas de ese subproceso lógico en un punto determinado de la duración de ese subproceso.

 contexto de código Proporciona una abstracción de una posición en el código conocido por el motor de depuración. Para la mayoría de las arquitecturas en tiempo de ejecución, un contexto de código es una dirección en la secuencia de instrucciones de un programa. Para los lenguajes no tradicionales, en los que el código puede no estar representado por instrucciones, un contexto de código puede estar representado por otros medios.

 Ruta de acceso de código Representa un punto de ejecución en el código donde se toma una bifurcación o se realiza una llamada de función. Un seguimiento de pila es esencialmente una lista de rutas de acceso de código de llamada de función.

 motor de depuración (DE) Un componente que permite la depuración de una arquitectura en tiempo de ejecución. Un motor de depuración funciona junto con el intérprete o el sistema operativo y proporciona servicios de depuración como control de ejecución, puntos de interrupción y evaluación de expresiones.

 contexto de documento Proporciona una abstracción de una posición en un documento de archivo de origen conocido por el motor de depuración. Para la mayoría de los idiomas, un contexto de documento es una posición en un archivo de origen. Para los idiomas no tradicionales, para los que el archivo de origen puede no ser texto, un contexto de documento puede estar representado por otros medios. Véase también *la posición del documento*.

 posición del documento Proporciona una abstracción de una posición en un archivo de origen conocido por el IDE. Para la mayoría de los idiomas, una posición de documento es una posición en un archivo de origen. Para los idiomas no tradicionales, una posición de documento puede representarse de otras maneras. Consulte también *contexto de documento*.

 punto de interrupción de error Una abstracción para describir un error en un punto de interrupción pendiente. Un punto de interrupción de error puede describir un error en la ubicación del punto de interrupción pendiente, la expresión asociada con el punto de interrupción pendiente u otra información que impide que el punto de interrupción pendiente se enlace a una ubicación de código.

 contexto de evaluación Proporciona una abstracción de un contexto de programación para la evaluación de expresiones. Normalmente, un contexto de evaluación es un ámbito. Al realizar la evaluación de expresiones en un contexto de expresión, el contexto de expresión proporciona reglas de ámbito que coinciden con su punto de creación. Por ejemplo, un contexto de expresión creado en un marco de pila proporcionará el contexto para evaluar variables locales, parámetros de método, miembros de clase (si procede) y variables globales.

 excepción interceptada Una excepción interceptada por un motor de depuración, incluso si no hay ningún mecanismo de control de excepciones en el marco de pila actual.

 JustMyCode El concepto de depurar solo el código que pertenece a un usuario e ignorar todo el código intermedio, como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.

 punto de interrupción pendiente Proporciona una abstracción para los puntos de interrupción antes, durante y después de cargar el código y una forma de virtualizar los puntos de interrupción. Un punto de interrupción pendiente:

- Contiene toda la información necesaria para enlazar un punto de interrupción al código en uno o varios programas.

- Puede enlazarse a varias ubicaciones de código en uno o más programas.

- Nunca se une al código.

  Cada vez que se carga el código, se comprueban todos los puntos de interrupción pendientes de un programa para ver si se pueden enlazar. Se dice que un punto de interrupción pendiente contiene todos los puntos de interrupción enlazados que enlaza.

  proceso Un proceso físico de Win32. Un proceso puede contener varios programas. Consulte también *programa*.

  programa Un único espacio de nombres que se ejecuta dentro de una arquitectura en tiempo de ejecución determinada. Consulte también *proceso*.

  Administrador de depuración de sesión (SDM) Administra cualquier número de motores de depuración depurando cualquier número de programas en varios procesos en cualquier número de máquinas. En el nivel básico, el SDM es un multiplexor de motores de depuración. Además, el SDM proporciona una vista unificada de la sesión de depuración al IDE.

  marco de pila Representa el estado de cálculo en un marco determinado y el nivel determinado de llamadas a funciones anidadas.

  subproceso La noción generalizada de ejecución de instrucciones basada en pilas que se ejecuta en al menos un programa.

  punto de interrupción de advertencia Una abstracción para describir una advertencia en un punto de interrupción pendiente. Un punto de interrupción de advertencia describe un motivo por el que el punto de interrupción pendiente aún no se ha enlazado a una ubicación de código. Esto puede ser que el código aún no se ha cargado para la ubicación descrita por el punto de interrupción pendiente, o por alguna otra razón.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
