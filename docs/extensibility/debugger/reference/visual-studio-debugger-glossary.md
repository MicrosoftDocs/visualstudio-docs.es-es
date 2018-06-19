---
title: Glosario de depurador de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 088f5d5a6b1edfc218b5dbe291d957d903f79702
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128194"
---
# <a name="visual-studio-debugger-glossary"></a>Glosario de depurador de Visual Studio
Los siguientes son los términos usados en el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuración.  
  
## <a name="terms"></a>Términos  
 punto de interrupción enlazado  
 Una abstracción para un punto de interrupción en el código. Hay una relación uno a uno entre un punto de interrupción enlazado y una instrucción de punto de interrupción en la secuencia de código. Cuando el código descarga, pueden deshacer el enlace de puntos de interrupción enlazados.  
  
 causalidad  
 Proporciona la capacidad para realizar el seguimiento de un subproceso lógico de ejecución a través de varias máquinas, procesos y subprocesos físicos y para reconstruir la pila de llamadas del subproceso lógico en un momento determinado de duración de dicho subproceso.  
  
 contexto de código  
 Proporciona una abstracción de una posición en el código que se sabe que el motor de depuración. Para la mayoría de las arquitecturas de tiempo de ejecución, un contexto de código es una dirección en la secuencia de instrucciones de un programa. Para los idiomas no tradicionales, en el que no se puede representar código de las instrucciones, se puede representar un contexto de código por otros medios.  
  
 ruta de acceso del código  
 Representa un punto de ejecución en el código donde se realiza una bifurcación o se realiza una llamada de función. Un seguimiento de pila es básicamente una lista de rutas de acceso del código de llamada de función.  
  
 motor de depuración (Alemania)  
 Un componente que permite la depuración de una arquitectura en tiempo de ejecución. Un motor de depuración funciona junto con el sistema operativo o intérprete y proporciona servicios de depuración como la evaluación de expresión, control y los puntos de interrupción de ejecución.  
  
 contexto de documento  
 Proporciona una abstracción de una posición en un documento de archivo de origen que sabe que el motor de depuración. Para la mayoría de los idiomas, un contexto de documento es una posición en un archivo de código fuente. Para los idiomas no tradicionales, para que el archivo de origen no puede ser texto, un contexto de documento puede estar representado por otros medios. Vea también *documento posición*.  
  
 posición del documento  
 Proporciona una abstracción de una posición en un archivo de origen que se sabe que el IDE. Para la mayoría de los idiomas, una posición del documento es una posición en un archivo de código fuente. Para los idiomas no tradicionales, una posición del documento puede estar representada de otras maneras. Vea también *contexto del documento*.  
  
 punto de interrupción de error  
 Una abstracción para describir un error en un punto de interrupción pendiente. Un punto de interrupción de error puede describir un error en la ubicación del punto de interrupción pendiente, la expresión asociada con el punto de interrupción pendiente u otra información que impide que el punto de interrupción pendiente de enlace a una ubicación del código.  
  
 contexto de evaluación  
 Proporciona una abstracción de un contexto de programación para la evaluación de expresión. Normalmente, un contexto de evaluación es un ámbito. Cuando se realiza la evaluación de expresiones en el contexto de una expresión, el contexto de expresiones proporciona las reglas de ámbito que coincide con su punto de creación. Por ejemplo, el contexto de una expresión que se creó en un marco de pila proporcionará el contexto para evaluar las variables locales, los parámetros de método, los miembros de clase (si procede) y variables globales.  
  
 excepción interceptada  
 Una excepción que intercepta un motor de depuración, incluso si ningún mecanismo de control de excepciones está en su lugar en el marco de pila actual.  
  
 JustMyCode  
 El concepto de depuración solo el código que pertenece a un usuario y Omitir todo el código intermedio como el código del sistema, incluso si el código fuente está disponible para ese código del sistema.  
  
 punto de interrupción pendiente  
 Proporciona una abstracción para los puntos de interrupción antes, durante y después de código está cargado y una manera para virtualizar los puntos de interrupción. Un punto de interrupción:  
  
-   Contiene toda la información necesaria para enlazar un punto de interrupción al código en uno o más programas.  
  
-   Puede enlazar a varias ubicaciones de código en uno o más programas.  
  
-   Nunca se enlaza propio al código.  
  
 Cada código en tiempo de carga, se comprueban todos los puntos de interrupción pendientes en un programa para ver si puede enlazar. Se dice que un punto de interrupción pendiente para que contenga todos los puntos de interrupción enlazados que enlaza.  
  
 proceso  
 Un proceso de Win32 físico. Un proceso puede contener varios programas. Vea también *programa*.  
  
 programa  
 Un espacio de nombres único ejecuta dentro de una determinada arquitectura de tiempo de ejecución. Vea también *proceso*.  
  
 Administrador de sesión de depuración (SDM)  
 Administra cualquier número de motores de depuración depuración cualquier número de programas en varios procesos en un número indeterminado de equipos. En el nivel básico, el SDM es un multiplexor de motores de depuración. Además, el SDM proporciona una vista unificada de la sesión de depuración para el IDE.  
  
 marco de pila  
 Representa el estado de cálculo en un marco determinado y un nivel concreto de llamadas a funciones anidadas.  
  
 subproceso  
 La noción generalizada de ejecución de instrucciones basada en pilas en al menos un programa.  
  
 punto de interrupción de advertencia  
 Una abstracción para describir una advertencia en un punto de interrupción pendiente. Un punto de interrupción de advertencia describe un motivo por qué el punto de interrupción pendiente no se ha enlazado a una ubicación del código. Esto puede deberse a que el código no ha cargado todavía para la ubicación descrita por el punto de interrupción pendiente o por algún otro motivo.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)