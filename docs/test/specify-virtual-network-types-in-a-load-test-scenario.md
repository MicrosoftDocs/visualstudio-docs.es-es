---
title: Especificar los tipos de red virtual en un escenario de prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 586038d325f17d37167166a361ee214d959ba2ab
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894682"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Especificar tipos de redes virtuales en un escenario de prueba de carga

La *combinación de redes* le ofrece una forma más realista de simular la carga en un escenario de prueba de carga. La carga se genera utilizando una combinación heterogénea de tipos de red en lugar de un tipo de red único. Se crea una aproximación más real a la forma en que los usuarios finales interactúan con las aplicaciones.

Una combinación de redes especifica la probabilidad de que un usuario virtual ejecute un *perfil de red* determinado. Un perfil de red es una simulación de ancho de banda de red en la capa de la aplicación. No simula latencia.

Cuando se crea una prueba de carga, es posible que se desee simular que la carga se genera a través de más de un tipo de conexión de red. La combinación de redes ofrece varios tipos de redes. Las distintas redes se simulan. Cuando se elige una opción como `Cable-DSL 1.5Mbps`, los tiempos de espera se insertan en la prueba para simular el ancho de banda seleccionado.

La combinación de redes funciona como otras opciones de combinación. Un tipo de red se selecciona de forma aleatoria asociada a un usuario virtual, basándose en la combinación de redes. Las pruebas de este usuario se ejecutan utilizando un tipo de red determinado, en función de la probabilidad que se haya especificado en la combinación.

Después de haber especificado una combinación de redes, puede agregar y quitar tipos de red. También puede cambiar la distribución de la combinación de redes utilizando el control de combinaciones.

El control de combinación permite ajustar con facilidad la distribución de las redes en un escenario.

Para más información, consulte [Control de combinaciones](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Emulación de red verdadera

Visual Studio usa emulación de red verdadera basada en software para todos los tipos de pruebas, incluidas las pruebas de carga. La emulación de red verdadera simula las condiciones de la red por manipulación directa de los paquetes de red. El emulador de red verdadera puede emular el comportamiento de las redes cableadas e inalámbricas utilizando un vínculo físico confiable, como Ethernet. En la emulación de red verdadera se incorporan los siguientes atributos de red:

-   Tiempo de ida y vuelta por la red (latencia)

-   Cantidad de ancho de banda disponible

-   Comportamiento de puesta en cola

-   Pérdida de paquetes

-   Reordenación de paquetes

-   Propagaciones de errores.

La emulación de red verdadera también proporciona flexibilidad en el filtrado de paquetes de red en función de las direcciones IP o de protocolos como TCP, UDP e ICMP.

Los desarrolladores y evaluadores de aplicaciones basados en red pueden utilizar la emulación de red verdadera para emular un entorno de pruebas deseado, evaluar el rendimiento, predecir el impacto de un cambio o tomar decisiones sobre la optimización de la tecnología. Cuando se compara con las bases de prueba de hardware, la emulación de red verdadera es una solución mucho más barata y flexible.

## <a name="to-add-new-networks-to-a-scenario"></a>Para agregar nuevas redes a un escenario

1.  Durante el proceso de especificación de la combinación de redes para un escenario, elija **Agregar**.

     Se agregará una nueva entrada de red a la cuadrícula.

    > [!NOTE]
    > Para mostrar el cuadro de diálogo **Editar combinación de redes**, haga clic con el botón derecho en un escenario existente y, luego, elija **Editar combinación de redes**.

2.  En la columna **Tipo de red**, elija la flecha de la nueva entrada. Elija el tipo de red que desea.

3.  (Opcional) Ajuste el control de combinación para especificar la distribución de pruebas. Para más información, consulte [Control de combinaciones](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4.  Cuando haya terminado de agregar redes, elija **Aceptar**.

## <a name="to-remove-networks-from-a-scenario"></a>Para quitar redes de un escenario

1.  Abra una prueba de carga.

2.  Haga clic con el botón derecho en el escenario del que quiere quitar una red y elija **Editar combinación de redes**. Aparecerá el cuadro de diálogo **Editar combinación de redes**.

3.  Seleccione la red en la cuadrícula y, luego, elija **Quitar**.

4.  (Opcional) Ajuste el control de combinación para especificar la distribución de pruebas. Para más información, consulte [Control de combinaciones](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5.  Cuando termine de quitar redes, elija **Aceptar**.

## <a name="about-the-mix-control"></a>Control de combinaciones

 El control de combinación permite ajustar el porcentaje de carga que se distribuye entre las pruebas, entre los tipos de exploradores o entre los tipos de redes en un escenario de prueba de carga. Para ajustar los valores de porcentajes, mueva los controles deslizantes. El ajuste de la combinación para los tipos de redes especifica la probabilidad de que un usuario virtual ejecute un perfil de red específico en un escenario de prueba de carga.

 Al mover un control deslizante, cambian los valores de porcentaje de todos los elementos disponibles. Si tiene más de dos elementos, la cantidad que agregue o quite se distribuirá uniformemente entre los demás elementos. Es posible reemplazar este comportamiento. Si activa la casilla de la columna de bloqueo de un elemento determinado, bloqueará el valor de porcentaje especificado para dicho elemento. Entonces, cuando mueva un control deslizante, la cantidad que agregue o quite sólo se aplicará a los elementos desbloqueados restantes.

 El botón **Distribuir** se usa para asignar los valores de porcentaje de forma equitativa entre todos los elementos. Por ejemplo, si tiene tres elementos, al elegir **Distribuir**, los valores de porcentaje se establecen en 34, 33 y 33.

> [!WARNING]
> El botón **Distribuir** reemplaza a cualquier elemento que esté bloqueado.

 También es posible escribir directamente los valores de porcentaje en la columna **%**, en lugar de usar los controles deslizantes. Si escribe un valor de porcentaje directamente, los demás elementos no se ajustarán automáticamente.

> [!NOTE]
> Los controles deslizantes se deshabilitan cuando el total no suma un 100 % o cuando los valores de porcentaje especificados en la columna **%** son decimales.

Si escribe los valores de porcentajes manualmente, debe asegurarse de que la suma de todos los elementos sea 100 %. Al guardar una combinación, si la suma no es igual al 100 %, se le solicitará que acepte los valores de porcentajes tal y como están o que vuelva a ajustarlos. Si decide aceptarlos tal y como están, se prorratearán al 100%.  Por ejemplo, si tiene dos elementos y los establece manualmente en un 80% y un 40%, el primer elemento se establecerá en un 66,67% (80 dividido entre 120) y el segundo elemento se establecerá en un 33,33% (40 dividido entre 120).