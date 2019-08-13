---
title: Diseño de XAML en Visual Studio y Blend
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0ff12b141a50872d586764d2b33bd68f3224fb
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821873"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Diseño de XAML en Visual Studio y Blend para Visual Studio

Las herramientas visuales de Visual Studio y Blend para Visual Studio permiten crear interfaces de usuario atractivas y experiencias multimedia enriquecidas con XAML para diversos tipos de aplicaciones. Ambos entornos de desarrollo integrado (IDE) comparten un conjunto de características en común, incluido un editor de XAML visual (diseñador). Blend para Visual Studio, que admite las plataformas WPF y UWP, brinda herramientas adicionales para diseñar estados visuales y crear animaciones.

Puede alternar entre Visual Studio y Blend para Visual Studio e incluso puede tener el mismo proyecto abierto en ambos IDE al mismo tiempo. Los cambios guardados en los archivos XAML en un IDE pueden aplicarse a través de recarga automática cuando se cambia al otro IDE. Para controlar el comportamiento de recarga, vaya a **Herramientas** > **Opciones** > **Entorno** > **Documentos** en cualquiera de los IDE.

## <a name="installation"></a>Instalación

- Para crear aplicaciones de WPF, instale la carga de trabajo **Desarrollo de escritorio de .NET** en Visual Studio. También se instalará Blend para Visual Studio.
- Para crear aplicaciones de UWP, instale la carga de trabajo **Desarrollo de Plataforma universal de Windows** en Visual Studio. También se instalará Blend para Visual Studio.
- Para crear aplicaciones de Xamarin.Forms, instale la carga de trabajo **Desarrollo para dispositivos móviles con .NET** en Visual Studio. Blend para Visual Studio *no* se instala. Blend no admite las aplicaciones de Xamarin.Forms.

## <a name="shared-capabilities"></a>Funcionalidades compartidas

Para realizar las tareas de desarrollo más fundamentales, Visual Studio y Blend para Visual Studio comparten el mismo conjunto de ventanas y funcionalidades, con ciertas diferencias sutiles. Entre los aspectos destacados se incluyen:

- **IntelliSense:** ambos IDE admiten funcionalidades de IntelliSense, como la finalización de instrucciones.

- **Debugging:** (Depuración) Puede depurar en [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) y en [Blend para Visual Studio](../debugger/debug-xaml-in-blend.md), incluido el establecimiento de puntos de interrupción en el código para depurar una aplicación en ejecución y el uso de [Recarga activa](../debugger/xaml-hot-reload.md) para cambiar el código XAML mientras se ejecuta la aplicación. Para mantener una experiencia de depuración coherente con Visual Studio, Blend para Visual Studio incluye la mayoría de las barras de herramientas y ventanas de depuración de Visual Studio.

- **Recarga de archivos:** puede editar los archivos XAML en Visual Studio o en Blend para Visual Studio. Los archivos editados guardados se recargan automáticamente cuando cambia entre los IDE. Para controlar el comportamiento de recarga, vaya a **Herramientas** > **Opciones** > **Entorno** > **Documentos** en cualquiera de los IDE.

- **Diseños y configuraciones sincronizados:** las preferencias de diseños y configuraciones de la ventana de herramientas personalizadas para Visual Studio o Blend para Visual Studio se sincronizan entre los dispositivos y las versiones cuando se inicia sesión con la misma cuenta de personalización. Vea [Sincronizar la configuración de Visual Studio en varios equipos](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Funcionalidades avanzadas de Blend para Visual Studio

Para aumentar la productividad, considere el uso de Blend para Visual Studio para las siguientes tareas. Estas son las áreas en las que Blend para Visual Studio ofrece más funcionalidad que el diseñador de Visual Studio o el código por sí solos.

| Tarea | Programa para la mejora | Blend para Visual Studio | Más información |
| - | - | - | - |
| **Diseñar estados visuales** | No hay ninguna herramienta que lo ayude a diseñar estados visuales, debe crearlos mediante programación. | Use las herramientas de diseño para cambiar la apariencia de un control según su estado. | [Estados visuales](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Crear animaciones** |No hay ninguna herramienta de diseño para animaciones; debe crearse mediante programación. Esto requiere tener conocimientos del sistema de animación y temporización en WPF y una amplia experiencia en codificación.|Puede crear animaciones visualmente y verlas previamente en Blend para Visual Studio. Esto es más rápido y preciso que la compilación de las animaciones en el código. Puede agregar desencadenadores para controlar la interacción del usuario y puede cambiar al código para agregar controladores de eventos y otras funciones.|[Animar objetos](../designers/animate-objects-in-xaml-designer.md)|
|**Convertir formas y texto en trazados para una manipulación más fácil**|No se admite.|Puede realizar cambios sutiles o espectaculares en las formas (como rectángulos y elipses) si las convierte en trazados, logrando así un mejor control de la edición. Puede cambiar la forma de los trazados, combinarlo y crear trazados compuestos de varias formas.<br /><br />También puede convertir bloques de texto en trazados para manipularlos como imágenes vectoriales.|[Dibujar formas y trazados](../designers/draw-shapes-and-paths.md)|
|**Editar controles, plantillas y estilos**|Requiere codificación y conocimientos de plantillas y estilos WPF.|Convierta cualquier imagen en un control.<br /><br />Utilice las herramientas de edición de plantillas para realizar cambios en controles, estilos y plantillas con unos pocos clics del ratón.<br /><br />Por ejemplo, puede usar recursos de estilo de Blend para Visual Studio para implementar controles WPF comunes (como botones, cuadros de lista, barras de desplazamiento, menús, etc.) y cambiar su color, estilo o plantilla subyacente directamente en Blend para Visual Studio. A continuación, puede cambiar a código para dar los últimos retoques si lo desea.|[Modificar el estilo de objetos](../designers/modify-the-style-of-objects-in-blend.md)|
|**Conectar la interfaz de usuario a los datos**|Puede crear un origen a partir de recursos como SQL Server Database, WCF o un servicio web, objeto o lista de SharePoint y, luego, enlace el origen de datos a los controles de la interfaz de usuario.<br /><br />Los datos en tiempo de diseño deben crearse manualmente para una experiencia de diseño interactivo.|En el caso de las aplicaciones de .NET Framework, cree datos de ejemplo de manera sencilla para crear prototipos y realizar pruebas. y cambie a datos reales cuando esté listo.<br /><br />Las capacidades de generación de datos de Blend para Visual Studio son excepcionales (puede agregar nombres, números, direcciones URL y fotografías de manera fácil y rápida) y pueden ahorrarle mucho tiempo.<br /><br />Para datos reales, puede enlazar los controles de interfaz de usuario a un archivo XML o a cualquier origen de datos CLR.|[Mostrar datos](../designers/display-data-in-blend.md)|

Para obtener más información sobre el diseño XAML avanzado, vea [Creación de una interfaz de usuario con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).
