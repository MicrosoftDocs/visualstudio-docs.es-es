---
title: Diseño de XAML en Visual Studio y en Blend para Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "82921368"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Diseño de XAML en Visual Studio y Blend para Visual Studio

Las herramientas visuales de Visual Studio y Blend para Visual Studio permiten crear interfaces de usuario atractivas y experiencias multimedia enriquecidas con XAML para diversos tipos de aplicaciones. Ambos entornos de desarrollo integrado (IDE) comparten un conjunto de características en común, incluido un editor de XAML visual (diseñador). Blend para Visual Studio, que admite las plataformas WPF y UWP, brinda herramientas adicionales para diseñar estados visuales y crear animaciones.

Puede alternar entre Visual Studio y Blend para Visual Studio e incluso puede tener el mismo proyecto abierto en ambos IDE al mismo tiempo. Los cambios guardados en los archivos XAML en un IDE pueden aplicarse a través de recarga automática cuando se cambia al otro IDE. Puede controlar el comportamiento de recarga Si navega a **herramientas** > **Opciones** > **entorno** > **documentos** en cualquiera de los dos IDE.

## <a name="installation"></a>Instalación

- Para crear aplicaciones de WPF, instale la carga de trabajo **Desarrollo de escritorio de .NET** en Visual Studio. También se instalará Blend para Visual Studio.

     ![Captura de pantalla de la carga de trabajo de desarrollo de escritorio de .NET desde el Instalador de Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Para crear aplicaciones de UWP, instale la carga de trabajo **Desarrollo de Plataforma universal de Windows** en Visual Studio. También se instalará Blend para Visual Studio.

     ![Captura de pantalla de la carga de trabajo de desarrollo de Plataforma universal de Windows desde el Instalador de Visual Studio](../xaml-tools/media/uwp-workload.png)

- Para crear aplicaciones de Xamarin.Forms, instale la carga de trabajo **Desarrollo para dispositivos móviles con .NET** en Visual Studio. Blend para Visual Studio *no* se instala. Blend no admite las aplicaciones de Xamarin.Forms.

     ![Captura de pantalla de la carga de trabajo desarrollo móvil con .NET desde el Instalador de Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Funcionalidades compartidas

Para realizar las tareas de desarrollo más fundamentales, Visual Studio y Blend para Visual Studio comparten el mismo conjunto de ventanas y funcionalidades, con ciertas diferencias sutiles. Estos son algunos de los aspectos destacados:

- **IntelliSense:** Ambos IDE admiten funciones de IntelliSense, como la finalización de instrucciones.

- **Depuración:** Puede depurar en [Visual Studio](inspect-xaml-properties-while-debugging.md) y [Blend para Visual Studio](../xaml-tools/debug-xaml-in-blend.md), incluida la configuración de puntos de interrupción en el código para depurar una aplicación en ejecución y usar la [recarga activa](../xaml-tools/xaml-hot-reload.md) para cambiar el código XAML mientras se ejecuta la aplicación. Para mantener una experiencia de depuración coherente con Visual Studio, Blend para Visual Studio incluye la mayoría de las barras de herramientas y ventanas de depuración de Visual Studio.

- **Recarga de archivos:** Puede editar los archivos XAML en Visual Studio o en Blend para Visual Studio. Los archivos editados guardados se recargan automáticamente cuando cambia entre los IDE. Puede controlar el comportamiento de recarga Si navega a **herramientas** > **Opciones** > **entorno** > **documentos** en cualquiera de los dos IDE.

- **Diseños y configuraciones sincronizados:** Los diseños y las preferencias de configuración de la ventana de herramientas de personalización de diseño para Visual Studio o Blend para Visual Studio se sincronizan en los dispositivos y versiones cuando se inicia sesión con la misma cuenta de personalización. Vea [Sincronizar la configuración de Visual Studio en varios equipos](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Funcionalidades avanzadas de Blend para Visual Studio

Para aumentar la productividad, considere el uso de Blend para Visual Studio para las siguientes tareas. Estas son las áreas en las que Blend para Visual Studio ofrece más funcionalidad que el diseñador de Visual Studio o el código por sí solos.

| Tarea | Visual Studio | Blend para Visual Studio | Más información |
| - | - | - | - |
| **Diseñar estados visuales** | No hay ninguna herramienta que lo ayude a diseñar estados visuales, debe crearlos mediante programación. | Use las herramientas de diseño para cambiar la apariencia de un control según su estado. | [Estados visuales](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Crear animaciones** |No hay ninguna herramienta de diseño para animaciones; debe crearse mediante programación. Esto requiere tener conocimientos del sistema de animación y temporización en WPF y una amplia experiencia en codificación.|Puede crear animaciones visualmente y verlas previamente en Blend para Visual Studio. Esto es más rápido y preciso que la compilación de las animaciones en el código. Puede agregar desencadenadores para controlar la interacción del usuario y puede cambiar al código para agregar controladores de eventos y otras funciones.|[Animar objetos](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Convertir formas y texto en trazados para una manipulación más fácil**|No compatible.|Puede realizar cambios sutiles o espectaculares en las formas (como rectángulos y elipses) si las convierte en trazados, logrando así un mejor control de la edición. Puede cambiar la forma de los trazados, combinarlo y crear trazados compuestos de varias formas.<br /><br />También puede convertir bloques de texto en trazados para manipularlos como imágenes vectoriales.|[Dibujar formas y trazados](../xaml-tools/draw-shapes-and-paths.md)|
|**Editar controles, plantillas y estilos**|Requiere codificación y conocimientos de plantillas y estilos WPF.|Convierta cualquier imagen en un control.<br /><br />Utilice las herramientas de edición de plantillas para realizar cambios en controles, estilos y plantillas con unos pocos clics del ratón.<br /><br />Por ejemplo, puede usar recursos de estilo de Blend para Visual Studio para implementar controles WPF comunes (como botones, cuadros de lista, barras de desplazamiento, menús, etc.) y cambiar su color, estilo o plantilla subyacente directamente en Blend para Visual Studio. A continuación, puede cambiar a código para dar los últimos retoques si lo desea.|[Modificar el estilo de objetos](modify-the-style-of-objects-in-blend.md)|
|**Conectar la interfaz de usuario a los datos**|Puede crear un origen a partir de recursos como SQL Server Database, WCF o un servicio web, objeto o lista de SharePoint y, luego, enlace el origen de datos a los controles de la interfaz de usuario.<br /><br />Los datos en tiempo de diseño deben crearse manualmente para una experiencia de diseño interactivo.|En el caso de las aplicaciones de .NET Framework, cree datos de ejemplo de manera sencilla para crear prototipos y realizar pruebas. y cambie a datos reales cuando esté listo.<br /><br />Las capacidades de generación de datos de Blend para Visual Studio son excepcionales (puede agregar nombres, números, direcciones URL y fotografías de manera fácil y rápida) y pueden ahorrarle mucho tiempo.<br /><br />Para datos reales, puede enlazar los controles de interfaz de usuario a un archivo XML o a cualquier origen de datos CLR.|[Mostrar datos](display-data-in-blend.md)|

Para obtener más información sobre el diseño XAML avanzado, vea [Creación de una interfaz de usuario con Blend para Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Consulte también

- [Información general sobre XAML](xaml-overview.md)
- [Introducción de Blend para Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
