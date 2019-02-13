---
title: Definición del tema de color y las fuentes
ms.date: 11/20/2017
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d8fcde39c2e64d431848b510b5e046031b6dac2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934073"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Inicio rápido: Personalización del IDE y el editor de Visual Studio

En esta guía de inicio rápido de entre cinco y diez minutos se personaliza el tema de color de Visual Studio mediante la selección del tema oscuro. También se personalizarán los colores de dos tipos diferentes de texto en el editor de texto.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="set-the-color-theme"></a>Establecimiento del tema de color

El tema de color predeterminado para la interfaz de usuario de Visual Studio 2017 se denomina **Azul**. Se va a cambiar a **Oscuro**.

1. En la barra de menús, que es la fila de menús, como **Archivo** y **Editar**, elija **Herramientas** > **Opciones**.

1. En la página de opciones **Entorno** > **General**, cambie la selección de **Tema de color** a **Oscuro** y, después, elija **Aceptar**.

   Se cambia el tema de color de todo el entorno de desarrollo (IDE) de Visual Studio a **Oscuro**.

   ![VS en tema oscuro](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Puede instalar temas predefinidos adicionales mediante la instalación de **Visual Studio Color Theme Editor** desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Después de instalar esta herramienta, aparecerán temas de color adicionales en la lista desplegable **Tema de color**.

## <a name="change-text-color"></a>Cambio del color del texto

Ahora se van a personalizar algunos colores de texto para el editor. En primer lugar, se va a crear un nuevo archivo XML para ver los colores predeterminados.

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Archivo**.

1. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija **Archivo XML** y, después, elija **Abrir**.

1. Pegue el código XML siguiente debajo de la línea que contiene `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Tenga en cuenta que los números de línea son de color azul turquesa y los atributos XML (como `id="bk101"`) son de color azul claro. Ahora se va a cambiar el color del texto de estos elementos.

   ![Colores de fuente del archivo XML](media/quickstart-personalize-xml-file.png)

1. Para abrir el cuadro de diálogo **Opciones**, elija **Herramientas** > **Opciones** en la barra de menús.

1. En **Entorno**, elija la categoría **Fuentes y colores**.

   Observe que el texto en **Show settings for** (Mostrar configuración para) reza **Text Editor** (Editor de texto), que es justamente lo que queremos. Expanda la lista desplegable solo para ver la extensa lista de lugares donde puede personalizar las fuentes y el color del texto.

1. Para cambiar el color del texto de números de línea, en la lista **Mostrar elementos**, elija **Número de línea**. En el cuadro **Primer plano del elemento**, elija **Oliva**.

   ![Cuadro de diálogo Opciones, Categoría Fuentes y colores](media/quickstart-personalize-line-number-color.png)

   Algunos lenguajes tienen sus propios valores específicos de fuentes y colores. Si es un desarrollador de C++ y quiere cambiar, por ejemplo, el color que se usa con las funciones, puede buscar **Funciones de C++** en la lista **Mostrar elementos**.

1. Antes de salir del cuadro de diálogo, vamos a cambiar también el color de los atributos XML. En la lista **Mostrar elementos**, desplácese hacia abajo hasta **Atributo XML** y selecciónelo. En el cuadro **Primer plano del elemento**, elija **Verde**. Seleccione **Aceptar** para guardar las selecciones y cerrar el cuadro de diálogo.

   Los números de línea son ahora de color oliva y los atributos XML son de color verde brillante. Si abre otro tipo de archivo, como un archivo de código C++ o C#, verá que los números de línea también aparecen en color oliva.

   ![Archivo XML con los nuevos colores de fuente](media/quickstart-personalize-xml-file-new-colors.png)

Hemos explorado solo un par de formas de personalizar los colores en Visual Studio. Esperamos que explore las otras opciones de personalización en el cuadro de diálogo **Opciones** para que Visual Studio sea realmente suyo.

## <a name="see-also"></a>Vea también

- [Personalizar el editor](../ide/customizing-the-editor.md)
- [Información general sobre IDE de Visual Studio](../get-started/visual-studio-ide.md)