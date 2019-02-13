---
title: Novedades de Live Unit Testing
ms.date: 10-11-2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 630213f05b2b3832e5b702cf2d6ef02a1996c98d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912838"
---
# <a name="whats-new-in-live-unit-testing"></a>Novedades de Live Unit Testing

En este tema se incluyen las nuevas características agregadas a Live Unit Testing en cada una de las versiones de Visual Studio a partir de la versión 15.3 de Visual Studio 2017. Para obtener información general sobre cómo utilizar Live Unit Testing, consulte [Live Unit Testing con Visual Studio 2017](live-unit-testing.md).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-154"></a>Novedades de Live Unit Testing para la versión 15.4 de Visual Studio 2017

A partir de la versión 15.4 de Visual Studio 2017, Live Unit Testing incluye mejoras en varias áreas:

- **Detectabilidad mejorada**. Para los usuarios que no conocen la existencia de la característica Live Unit Testing, el IDE de Visual Studio muestra una barra dorada que menciona esta característica cada vez que el usuario abre una solución que incluye pruebas unitarias y Live Unit Testing no está activada. La información presentada en la barra dorada permite al usuario para obtener más información sobre Live Unit Testing y habilitarla. La barra dorada también muestra información cuando no se cumplen los requisitos previos de Live Unit Testing. Se incluyen los siguientes:

   - Faltan los adaptadores de prueba.
   - Están presentes versiones anteriores de los adaptadores de prueba.
   - Se necesita una restauración de los paquetes de NuGet a los que hace referencia la solución. 

- **Integración con las notificaciones del centro de tareas**. El IDE de Visual Studio muestra ahora una notificación de procesamiento en segundo plano de Live Unit Testing en el centro de tareas para que los usuarios sepan fácilmente lo que está ocurriendo cuando se habilita Live Unit Testing. Esto aborda el problema principal de iniciar Live Unit Testing en una solución de gran tamaño. Anteriormente, durante varios minutos hasta que aparecían los iconos de cobertura, los usuarios no podían determinar si realmente se había habilitado Live Unit Testing y si funcionaba. Este problema ya no existe.

- **Compatibilidad con la versión 1 del marco MSTest**: Live Unit Testing ya funciona con tres populares marcos de pruebas unitarias: xUnit, NUnit y MSTest. Anteriormente, Live Unit Testing solo funcionaba cuando los proyectos de prueba unitaria de MSTest usaban la versión 2 de MSTest. A partir de la versión 15.4 de Visual Studio 2017, también es compatible con la versión 1 de MSTest. 

- **Rendimiento y confiabilidad**: Ahora Live Unit Testing garantiza que el sistema puede detectar mejor los casos en que los proyectos no han terminado de cargarse totalmente y evita el bloqueo de Live Unit Testing. Las mejoras en el rendimiento de compilación también evitan que se vuelvan a evaluar los proyectos de MSBuild cuando el sistema sepa que no ha cambiado nada en el archivo del proyecto.  

- **Perfeccionamientos varios de la interfaz de usuario**:  La confusa opción **Live Test Set – Include/Exclude** (Conjunto de pruebas en directo: incluir/excluir) desde el gesto contextual ha cambiado a **Live Unit Testing Include/Exclude** (Live Unit Testing: incluir/excluir). Se ha quitado la opción **Reset clean** (Restablecer limpieza) del menú **Prueba** > **Live Unit Testing**. Ahora se puede acceder a ella seleccionando **Herramientas** > **Opciones** > **Live Unit Testing** y **Delete Persisted Data** (Eliminar datos persistentes).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>Novedades de Live Unit Testing para la versión 15.3 de Visual Studio 2017

A partir de la versión 15.3 de Visual Studio 2017, Live Unit Testing incluye mejoras en dos áreas principales:

- Compatibilidad con .NET Core y .NET Standard. Puede usar Live Unit Testing en soluciones de .NET Core y .NET Standard escritas en C# o Visual Basic.
 
-  Mejoras en el rendimiento. Observará que el rendimiento es significativamente más rápido después de la primera compilación completa y la ejecución de las pruebas en Live Unit Testing. También notará una mejora significativa en el rendimiento en los inicios posteriores de Live Unit Testing en la misma solución. Ahora conservamos los datos que genera Live Unit Testing y los volvemos a usar tantas veces como sea posible con comprobaciones actualizadas. 
 
Además de estas incorporaciones principales, Live Unit Testing incluye las siguientes mejoras: 

- Ahora se usa un nuevo icono de probeta para distinguir el método de prueba de los métodos regulares. Un icono de probeta vacío indica que la prueba específica no se incluye en Live Unit Testing. 

- Al hacer clic en un método de prueba desde la ventana de interfaz de usuario emergente de un icono de cobertura de Live Unit Testing, ahora tiene la opción de depurar la prueba directamente desde ese contexto dentro de la ventana de la interfaz de usuario y sin tener que salir del editor de código. Esto es especialmente útil cuando se trata de una prueba con errores.  

- Se han agregado varias opciones configurables a Herramientas/Opciones/Live Unit Testing/General. Puede limitar la memoria que se usa para Live Unit Testing. También puede especificar la ruta de acceso de archivo para los datos persistentes de Live Unit Testing para su solución abierta. 

- Se han agregado varios elementos de menú adicionales a la barra de menús de Prueba/Live Unit Testing. **Reset Clean**  (Restablecer limpieza) elimina los datos persistentes y los genera de nuevo. **Opción** salta a Herramientas/Opciones/Live Unit Testing/General.
  
- Ahora puede usar los siguientes atributos para especificar en el código fuente que desea excluir métodos de prueba de destino de Live Unit Testing:
   - Para xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Para NUnit: `[Category("SkipWhenLiveUnitTesting")]`
   - Para MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vea también
- [Presentación de Live Unit Testing](live-unit-testing-intro.md)   
- [Live Unit Testing con Visual Studio 2017](live-unit-testing.md)
