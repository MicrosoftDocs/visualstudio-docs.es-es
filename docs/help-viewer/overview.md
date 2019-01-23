---
title: Documentación de la ayuda sin conexión
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc9fd8b8684782f92c27563fb5d19a46d61c554e
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/13/2018
ms.locfileid: "54406123"
---
# <a name="microsoft-help-viewer"></a>Visor de Ayuda de Microsoft

Puede instalar y ver el contenido de distintos productos y tecnologías en el equipo local usando el Visor de Ayuda de Microsoft. Estos productos incluyen Visual Studio, .NET Framework, referencia del lenguaje, SQL Server y Desarrollo de Windows. El Visor de Ayuda le permite:

- Descargar conjuntos de contenido, que también se conocen como libros. Esto puede ser útil si tiene que trabajar "sin conexión" y seguir teniendo acceso a la documentación.

- Examinar y buscar en la tabla de contenido para buscar temas por título.

- Buscar temas en el índice.

- Buscar información mediante la búsqueda de texto completo.

- Ver, marcador e imprimir temas.

Para instalar el Visor de Ayuda, vea [Instalación del Visor de Ayuda de Microsoft](../help-viewer/installation.md). Para empezar a leer temas de ayuda en el Visor de Ayuda, en lugar de en línea, vaya al menú **Ayuda** de Visual Studio y, después, elija **Establecer preferencias de la Ayuda** > **Iniciar en el Visor de Ayuda**.

> [!TIP]
> Otra forma de descargar contenido localmente para poder verlo sin conexión a Internet es descargarlo en versión PDF. Muchos conjuntos de la documentación de docs.microsoft.com incluyen un vínculo en la parte inferior de la tabla de contenido (TDC) para descargar un archivo PDF que contiene todos los artículos de dicha tabla.
>
> ![Descargar PDF para la documentación de Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Paseo por el Visor de Ayuda

Puede buscar información en el contenido instalado mediante las pestañas de navegación, ver contenido instalado en la pestaña o pestañas de tema y administrar contenido mediante el uso de la pestaña **Administrar contenido**. También puede realizar tareas adicionales mediante los botones en la barra de herramientas y encontrar información adicional en la esquina inferior derecha de la ventana.

### <a name="navigation-tabs"></a>Pestañas de navegación

|Tab|Descripción|
|---|-----------|
|Contenido|Muestra el contenido instalado como una jerarquía (tabla de contenido). Puede especificar criterios para filtrar los títulos que aparecen.|
|Índice|Muestra una lista alfabética de términos indexados. Puede buscar en el índice, especificar criterios para filtrar las entradas y requerir que las entradas contengan o empiecen con el texto que se especifica.|
|Favoritos|También puede añadir temas a Favoritos. Para ello, elija el botón **Agregar a Favoritos**. Los temas aparecerán en esta pestaña. En la sección **Historial** se muestra una lista de los temas que ha visualizado recientemente.|
|Buscar|Proporciona un cuadro de búsqueda en el que puede buscar términos en cualquier lugar del contenido, incluidos los títulos de temas y el código.|

### <a name="view-topics"></a>Ver temas

Cada tema aparece en su propia pestaña, y puede abrir varios temas a la vez.

### <a name="manage-content"></a>Administrar contenido

Puede instalar, actualizar, mover y eliminar contenido mediante la pestaña **Administrar contenido**. En la parte superior de la pestaña, puede usar el control **Origen de instalación** para especificar si quiere instalar los libros desde una ubicación de red o desde un disco o URI. El cuadro **Ruta de acceso del almacén local** muestra donde se instalarán los libros en el equipo local y puede moverlos a una ubicación diferente con el botón **Mover**.

La lista de contenido muestra qué libros puede instalar o ya instaló, si hay disponible alguna actualización y el tamaño de cada libro. Puede instalar o quitar uno o más libros pulsando los vínculos **Agregar** o **Quitar** y, después, seleccionando el botón **Actualizar** en el panel **Cambios pendientes**. Si hay actualizaciones disponibles para los libros que ya instaló, puede actualizar ese contenido seleccionando el vínculo **Haga clic aquí para descargar ahora** en la parte inferior de la ventana. Además, todos los libros instalados se actualizan si hay actualizaciones disponibles al instalar libros adicionales.

> [!NOTE]
> La funcionalidad de la pestaña **Administrar contenido** puede diferir si el administrador del Visor de Ayuda desactiva estas características o si no tiene acceso a Internet.

### <a name="toolbar-buttons"></a>Botones de barra de herramientas

La barra de herramientas de la ventana **Visor de Ayuda** contiene los siguientes botones:

- El botón **Mostrar tema en contenido** muestra la ubicación del tema en la pestaña **Contenido**.

- El botón **Agregar a favoritos** agrega el tema activo a la pestaña **Favoritos**.

- El botón **Buscar en tema** resalta el texto de búsqueda en el tema activo.

- El botón **Imprimir** imprime o muestra una vista previa del tema activo.

- El botón **Opciones del Visor** muestra la configuración como la del tamaño de texto, cuántos resultados de búsqueda se devuelven, cuántos temas se muestran en el historial y si se debe comprobar si hay actualizaciones en línea.

- El botón **Administrar contenido** activa la pestaña **Administrar contenido**.

- El pequeño triángulo que aparece a la derecha abre una lista de pestañas, incluidas las del tema y la correspondiente a **Administrar contenido**. Puede elegir un nombre de pestaña y convertirla en la pestaña activa.

## <a name="see-also"></a>Vea también

- [Instalación del Visor de Ayuda de Microsoft](../help-viewer/installation.md)
- [Guía del administrador del Visor de Ayuda](../help-viewer/administrator-guide.md)
- [Instalar y administrar el contenido local](../help-viewer/install-manage-local-content.md)
