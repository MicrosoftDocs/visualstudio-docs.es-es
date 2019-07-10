---
title: Personalización del IDE
description: Visual Studio para Mac puede personalizarse de varias formas, lo que permite a los usuarios desarrollar aplicaciones en un entorno que satisfaga a la vez sus necesidades de eficiencia y estéticas. En este tema se analizan las diversas formas en que Visual Studio para Mac puede adaptarse para satisfacer las necesidades del usuario.
author: alanjclark
ms.author: alcl
ms.date: 05/06/2018
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: ff0c7a2970a9ecfdfb9de08f487ad7dfbe768249
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67691836"
---
# <a name="customizing-the-ide"></a>Personalización del IDE

Visual Studio para Mac puede personalizarse de varias formas, lo que permite a los usuarios desarrollar aplicaciones en un entorno que satisfaga a la vez sus necesidades de eficiencia y estéticas. En este artículo se analizan las diversas formas en que Visual Studio para Mac puede adaptarse para satisfacer las necesidades del usuario.

## <a name="dark-theme"></a>Tema oscuro

![Vista Tema oscuro](media/customizing-the-ide-image7a.png)

Puede cambiar los temas de Visual Studio para Mac si va a **Visual Studio > Preferencias > Entorno > Estilo visual** y selecciona el tema que quiere en la lista desplegable **Tema de la interfaz de usuario**, como se muestra en la imagen siguiente:

![Selección de Tema oscuro](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localización

Visual Studio para Mac se ha localizado a los siguientes 14 idiomas, con lo que resulta accesible para más desarrolladores:

* Chino (China)
* Chino (Taiwán)
* Checo
* Francés
* Alemán
* Inglés
* Italiano
* Japonés
* Coreano
* Polaco
* Portugués (Brasil)
* Ruso
* Español
* Turco

Para cambiar el idioma mostrado en Visual Studio para Mac, vaya a **Visual Studio > Preferencias > Entorno > Estilo visual** y seleccione el idioma que quiere en la lista desplegable **Idioma de la interfaz de usuario**, como se muestra en la imagen siguiente:

![Selección de idioma](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Información del autor

El panel Información del autor permite agregar información relevante sobre uno mismo, como el nombre, la dirección de correo electrónico, el propietario de los derechos de autor del trabajo, la empresa y la marca comercial:

![Edición de la sección Información del autor](media/customizing-the-ide-image9a.png)

Esta información se usa para rellenar encabezados de archivo estándar, como una licencia, que se pueden agregar a nuevos archivos:

![Opciones de encabezado estándar](media/customizing-the-ide-image8a.png)

Los campos **Nombre** y **Correo electrónico** se usarán para agregar información a cualquier confirmación realizada mediante el control de versiones de Visual Studio para Mac. Si no ha rellenado estos campos, Visual Studio para Mac le pedirá que lo haga cuando intente usar el control de versiones.

## <a name="key-bindings"></a>Enlaces de teclado

Los enlaces de teclado permiten adaptar el entorno de desarrollo para desplazarse de forma más eficaz por Visual Studio para Mac. Proporciona enlaces de teclado conocidos para muchos IDE populares, como Visual Studio (en Windows), ReSharper, Visual Studio Code y Xcode.

Los enlaces de teclado se pueden establecer si se va a **Visual Studio > Preferencias > Entorno > Enlaces de teclado**, como se muestra en la imagen siguiente:

![Establecimiento de enlaces de teclado](media/customizing-the-ide-image10a.png)

Desde ahí se pueden buscar combinaciones de enlaces de teclado, ver enlaces en conflicto, agregar nuevos enlaces y editar los enlaces existentes.

## <a name="workspace-layout"></a>Diseño del área de trabajo

El área de trabajo de Visual Studio para Mac consta de un área de documento principal (normalmente el editor, la superficie del diseñador o el archivo de opciones), rodeada de *paneles* complementarios que contienen información útil para acceder a los archivos de la aplicación y administrarlos, probar y depurar.

 ![Diseño del área de trabajo](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>Visualización y organización de paneles

Al abrir cualquier solución o archivo nuevos en Visual Studio para Mac, debería observar algunos *paneles* en el área de trabajo, incluidos el Panel de solución, Esquema del documento y Errores:

![Paneles de solución](media/customizing-the-ide-image2a.png)

Visual Studio para Mac proporciona paneles que contienen información adicional, herramientas y ayudas de navegación y a los que se accede al ir al elemento de menú **Vista > Paneles** y seleccionar un panel para agregarlo:

![Selección de nuevo panel](media/customizing-the-ide-image3a.png)

Los paneles también se pueden abrir automáticamente mediante varios comandos, como **Buscar en archivos** (Mayús + Cmd + F), que abre un panel separado de resultados de búsqueda.

Los paneles se pueden mover y organizar por el flujo de trabajo de la forma que resulte más útil para el usuario. Por ejemplo, se pueden acoplar en cualquier lado del editor de documentos, junto a otro panel, encima o debajo de otro panel o como un conjunto de paneles con pestañas que permitan cambiar de panel rápidamente.

En el caso de los paneles usados con frecuencia, se pueden separar por completo de la ventana de Visual Studio para Mac y se pueden crear ventanas independientes para ellos.

Los paneles se pueden ocultar y cerrar con los controles de la esquina superior derecha de cada panel:

![Ocultación y cierre de paneles](media/customizing-the-ide-image5a.png)

Los paneles ocultados automáticamente están acoplados a los lados del área de trabajo para que sean fácilmente accesibles cuando se necesiten. Si se mantiene el puntero sobre el panel, este se muestra de nuevo, y se oculta cuando pierde el foco del teclado y el mouse.

### <a name="organizing-layouts"></a>Organización de diseños

Los paneles que se muestran en todo momento dependen del contexto actual. Por ejemplo, cuando se usa el diseñador visual, los paneles de cuadro de herramientas y de cuadrícula de propiedades son más importantes; al depurar, resulta útil tener los paneles del depurador para ver la pila y las variables locales.

El estado de los paneles abiertos se representa mediante un *diseño*. Se puede cambiar de diseño manualmente mediante el menú Vista, como se muestra en la imagen siguiente, o de forma automática al realizar una acción, como depurar o abrir un guion gráfico:

![Selección de nuevos diseños](media/customizing-the-ide-image6b.png)

Siempre hay un diseño activo y cualquier cambio realizado en un diseño, como agregar o cambiar la posición de un panel, solo cambia el diseño activo. Una vez que se cierra Visual Studio para Mac, los cambios realizados no se guardan.

Pero es posible crear un nuevo diseño mediante el elemento de menú **Vista > Guardar diseño actual**. Con esto se agrega el diseño actual al menú para que se pueda seleccionar en cualquier momento:

![Guardado del diseño actual](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Compatibilidad con la edición en paralelo

Visual Studio para Mac permite abrir editores de texto en paralelo o tener un editor como una ventana flotante separada.

Se puede habilitar el modo de dos columnas mediante el elemento de menú Vista si se selecciona **Vista > Columnas del editor > 2 columnas** o si se arrastra una pestaña del editor a uno de los bordes del área de este:

![Modo de dos columnas en paralelo](media/customizing-the-ide-sbs.png)

Las pestañas del editor se pueden arrastrar fuera del área de documento para crear una ventana flotante del editor. Esta ventana flotante también admite editores en paralelo y puede contener varias pestañas del editor:

![Creación de nueva ventana](media/customizing-the-ide-sbs1.png)

![Dos columnas en paralelo con pestañas adicionales](media/customizing-the-ide-sbs2.png)

Para revertir a un único editor abierto, seleccione **Vista > Columnas del editor > 1 columna**.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>Vea también

- [Personalizar el IDE de Visual Studio (en Windows)](/visualstudio/ide/personalizing-the-visual-studio-ide)