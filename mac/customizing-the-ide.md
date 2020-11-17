---
title: Personalización del IDE
description: Visual Studio para Mac puede personalizarse de varias formas, lo que permite a los usuarios desarrollar aplicaciones en un entorno que satisfaga a la vez sus necesidades de eficiencia y estéticas. En este artículo se analizan las diversas formas en que Visual Studio para Mac puede adaptarse para satisfacer las necesidades del usuario.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2020
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.custom: video
ms.openlocfilehash: 05fd1091a279a085c2a727eb36cbc56fcb201057
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493325"
---
# <a name="customizing-the-ide"></a>Personalización del IDE

Visual Studio para Mac puede personalizarse, lo que permite a los usuarios desarrollar aplicaciones en un entorno que satisfaga a la vez sus necesidades de eficiencia y estéticas. En este artículo se analizan las diversas formas en que Visual Studio para Mac puede adaptarse para satisfacer las necesidades del usuario.

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

Los enlaces de teclado, o métodos abreviados de teclado, permiten adaptar el entorno de desarrollo para desplazarse de forma más eficaz por Visual Studio para Mac. Proporciona enlaces de teclado conocidos para muchos IDE populares, como Visual Studio (en Windows), ReSharper, Visual Studio Code y Xcode.

Los enlaces de teclado se pueden establecer si se va a **Visual Studio > Preferencias > Entorno > Enlaces de teclado**, como se muestra en la imagen siguiente:

![Establecimiento de enlaces de teclado](media/customizing-the-ide-image10a.png)

Desde ahí se pueden buscar combinaciones de enlaces de teclado, ver enlaces en conflicto, agregar nuevos enlaces y editar los enlaces existentes.

Estos enlaces también se pueden establecer durante la configuración inicial de Visual Studio para Mac, a través de la pantalla **Selección de teclado**:

![Establecimiento de enlaces de teclado, primera ejecución](media/ide-tour-2019-keyboard-shortcut.png)

## <a name="workspace-layout"></a>Diseño del área de trabajo

El área de trabajo de Visual Studio para Mac consta de un área de documento principal (normalmente el editor, la superficie del diseñador o el archivo de opciones), rodeada de *ventanas de herramientas* complementarias que contienen información de utilidad para acceder a los archivos de aplicación y administrarlos, probar y depurar.

 ![Diseño del área de trabajo](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-tool-windows"></a>Visualización y organización de las ventanas de herramientas

Al abrir una solución o un archivo nuevos en Visual Studio para Mac, debería observar algunas *ventanas de herramientas* en el área de trabajo, como la ventana de la solución, Esquema del documento y Errores:

![Ventana de herramientas](media/customizing-the-ide-image2a.png)

Visual Studio para Mac proporciona ventanas de herramientas que contienen información adicional, herramientas y ayudas de navegación, y a las que se accede al ir al elemento de menú **Vista** y seleccionar una ventana de herramientas para agregarla:

![Selección de nueva ventana de herramientas](media/customizing-the-ide-image3a.png)

Las ventanas de herramientas también se pueden abrir automáticamente mediante varios comandos, como **Buscar en archivos** (Mayús + Cmd + F), que abre una ventana desasociada de resultados de búsqueda.

Las ventanas de herramientas se pueden mover y organizar por el flujo de trabajo de la forma que resulte más útil para el usuario. Por ejemplo, se pueden acoplar en cualquier lado del editor de documentos, junto a otra ventana de herramientas, encima o debajo de otra ventana o como un conjunto de ventanas con pestañas que permiten alternar rápidamente entre ellas.

Las ventanas de herramientas usadas con frecuencia también se pueden desasociar por completo de la ventana de Visual Studio para Mac y aparecer como una nueva ventana.

Las ventanas de herramientas se pueden anclar y cerrar mediante los controles de la esquina superior derecha de cada ventana:

:::image type="content" source="media/customizing-the-ide-image5a.png" alt-text="Uso de controles para anclar o cerrar ventanas de herramientas":::

Las ventanas ancladas se acoplan a los lados del área de trabajo y permanecen abiertas para un acceso más rápido cuando se necesitan. Las ventanas desancladas están acopladas, pero no se muestran hasta que se mantiene el mouse sobre la pestaña de la ventana o se enfocan con el teclado; pueden ocultarse cuando el foco del mouse y el teclado las abandona.

### <a name="organizing-layouts"></a>Organización de diseños

Las ventanas de herramientas que se muestran en todo momento dependen del contexto actual. Por ejemplo, cuando se usa el diseñador visual, las ventanas de cuadro de herramientas y de cuadrícula de propiedades son las más importantes; al depurar, resulta útil tener las ventanas del depurador para ver la pila y las variables locales.

El estado de las ventanas de herramientas abiertas se representa mediante un *diseño*. Se puede cambiar de diseño manualmente mediante el menú Vista, como se muestra en la imagen siguiente, o de forma automática al realizar una acción, como depurar o abrir un guion gráfico:

![Selección de nuevos diseños](media/customizing-the-ide-image6b.png)

Es posible crear un nuevo diseño mediante el elemento de menú **Vista > Diseño > Guardar diseño actual...** Este comando agrega el diseño actual al menú para que se pueda seleccionar en cualquier momento:

![Guardado del diseño actual](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Compatibilidad con la edición en paralelo

Visual Studio para Mac permite abrir editores de texto en paralelo o tener un editor como una ventana flotante separada.

El modo de dos columnas se puede habilitar mediante el elemento de menú Vista; seleccione **Vista > Columnas del editor > 2 columnas** o arrastre una pestaña del editor a uno de los bordes del área de este:

![Modo de dos columnas en paralelo](media/customizing-the-ide-sbs.png)

Las pestañas del editor se pueden arrastrar fuera del área de documento para crear una ventana flotante del editor. Esta ventana flotante también admite editores en paralelo y puede contener varias pestañas del editor:

![Creación de nueva ventana](media/customizing-the-ide-sbs1.png)

![Dos columnas en paralelo con pestañas adicionales](media/customizing-the-ide-sbs2.png)

Para revertir a un único editor abierto, seleccione **Vista > Columnas del editor > 1 columna**.

## <a name="related-video"></a>Vídeo relacionado

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Customize-the-Look-and-Feel/player]

## <a name="see-also"></a>Vea también

- [Personalizar el IDE de Visual Studio (en Windows)](/visualstudio/ide/personalizing-the-visual-studio-ide)