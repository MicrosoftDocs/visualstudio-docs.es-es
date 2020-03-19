---
title: IntelliSense de C++
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: c0d1be12f733a858bf223fb1dce6a091c0dc6c50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594219"
---
# <a name="visual-c-intellisense-features"></a>Características de IntelliSense de Visual C++

IntelliSense es el nombre que se le da a un conjunto de características que hacen que codificar sea más práctico. IntelliSense para C++ está disponible para los archivos independientes y para los archivos que forman parte de un proyecto de C++. En proyectos multiplataforma, algunas características de IntelliSense están disponibles en archivos *.cpp* y *.c* en el proyecto de código compartido, aun cuando el usuario se encuentre en un contexto de Android o iOS.

Este artículo proporciona información general de las características de IntelliSense en C++. Para obtener información sobre cómo configurar el proyecto para IntelliSense y cómo solucionar problemas, consulte [Configure a C++ project for IntelliSense](visual-cpp-intellisense-configuration.md) (Configuración de un proyecto de C++ para IntelliSense).

## <a name="intellisense-features-in-c"></a>Características de Intellisense en C++

IntelliSense es el nombre que se le da a un conjunto de características que hacen que codificar sea más práctico. Dado que cada persona puede tener una idea diferente de lo que es práctico, casi todas las características de IntelliSense pueden habilitarse o deshabilitarse en el cuadro de diálogo **Opciones**, bajo **Editor de texto** > **C/C++**  > **Avanzado**. El cuadro de diálogo **Opciones** está disponible en el menú **Herramientas** de la barra de menús.

![Cuadro de diálogo Herramientas > Opciones](../ide/media/sintellisensecpptoolsoptions.PNG)

Puede utilizar los elementos de menú y métodos abreviados de teclado que se muestran en la siguiente imagen para acceder a IntelliSense.

![Menú de IntelliSense](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>Lista de finalización de instrucciones y de miembros

Cuando empiece a escribir una palabra clave, un tipo, una función, el nombre de una variable u otro elemento de programa que el compilador reconozca, el editor le ofrecerá la opción de completar la palabra automáticamente.

Para ver una lista de los iconos y sus significados, vea [Iconos de la Vista de clases y del Examinador de objetos](../ide/class-view-and-object-browser-icons.md).

![Ventana Palabra completa de Visual C&#43;&#43;](../ide/media/vs2015_cpp_complete_word.png)

La primera vez que se invoca la lista de miembros solo muestra los miembros a los que se puede acceder en el contexto actual. Si presiona**Ctrl**+**J** a continuación, aparecen todos los miembros, independientemente de su accesibilidad. Si se invoca una tercera vez, se muestra una lista de elementos de programa aún más amplia. Puede desactivar la lista de miembros en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++**  > **General** > **Lista de miembros automática**.

![Lista de miembros de Visual C&#43;&#43;](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>Ayuda de parámetros

Cuando se escribe una llave de apertura de una llamada de función o un corchete angular en una declaración de variable de plantilla de clase, el editor muestra una pequeña ventana con los tipos de parámetros para cada sobrecarga de la función o el constructor. El parámetro "actual" &mdash;basado en la ubicación del cursor&mdash; está en negrita. Puede desactivar la información de parámetros en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++**  > **General** > **Información de parámetros**.

![Ayuda de parámetros de Visual C&#43;&#43;](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>Información rápida

Cuando coloca el cursor del mouse sobre una variable, se muestra una pequeña ventana en línea que muestra la información de tipo y el encabezado en el que se define el tipo. Para ver la firma de la función, coloque el puntero sobre una llamada a función. Puede desactivar la información rápida en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++**  > **Avanzado** > **Información rápida automática**.

![InformaciónRápida de Visual C&#43;&#43;](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>Subrayados ondulados de error

Los subrayados ondulados bajo un elemento de programa (variable, palabra clave, llave, nombre de tipo, etc.), intentan indicarle la existencia de un error o un posible error en el código. Un subrayado ondulado aparece cuando escribe una declaración adelantada, para recordarle que aún le queda por escribir la implementación. Un subrayado ondulado de color púrpura se muestra en un proyecto compartido para indicar que hay un error en código que no está activo actualmente, como sucede, por ejemplo, cuando está trabajando en el contexto de Windows pero introduce algo que sería un error en un contexto de Android. Un subrayado ondulado de color rojo indica una advertencia o un error del compilador en el código activo que tiene que resolver.

![Líneas de subrayado de errores de Visual C&#43;&#43;](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>Coloración y fuentes de código

Se pueden cambiar los colores y las fuentes predeterminados en el cuadro de diálogo **Opciones**, en **Entorno** > **Fuentes y colores**. Puede cambiar las fuentes de muchas ventanas de interfaz de usuario, no solo las del editor. Los ajustes específicos de C++ comienzan con "C++"; el resto de ajustes es para todos los lenguajes.

## <a name="cross-platform-intellisense"></a>IntelliSense multiplataforma

En un proyecto de código compartido, algunas características de IntelliSense, como los subrayados ondulados, están disponibles incluso cuando se está trabajando en un contexto de Android. Si escribe código que produciría un error en un proyecto inactivo, IntelliSense mostrará subrayados ondulados de todos modos, pero en un color distinto al de los subrayados ondulados de errores del contexto actual.

Considere una aplicación de OpenGLES que está configurada para compilarse para Android y iOS. La ilustración muestra el código compartido que se está editando. En esta imagen, el proyecto activo es **iOS.StaticLibrary**:

![iOS está seleccionado como el proyecto activo.](../ide/media/intellisensecppcrossplatform2.png)

Tenga en cuenta lo siguiente:

- La rama `#ifdef` de la línea 6 aparece en gris para indicar que se trata de una región inactiva porque no se ha definido `__ANDROID__` para el proyecto de iOS.

- La variable de saludo de la línea 11 se inicializa con el identificador `HELLO`, que ahora tiene un subrayado ondulado de color rojo. Esto se debe a que no se ha definido ningún identificador `HELLO` en el proyecto de iOS actualmente activo.

- La línea 12 tiene un subrayado ondulado de color púrpura en el identificador `BYE` porque este identificador no está definido en el proyecto **Android.NativeActivity** (actualmente) inactivo. Aunque esta línea se compila cuando iOS es el proyecto activo, no se compilará cuando Android sea el proyecto activo. Puesto que se trata de código compartido, debe corregir el código aunque se compile en la configuración activa actualmente.

Si cambia el proyecto activo a Android, cambiarán los subrayados ondulados:

- La rama `#else` de la línea 8 aparece en gris para indicar que se trata de una región inactiva porque se ha definido `__ANDROID__` para un proyecto de Android.

- La variable de saludo de la línea 11 se inicializa con el identificador `HELLO`, que tiene un subrayado ondulado de color púrpura. Esto se debe a que no se ha definido ningún identificador `HELLO` en el proyecto de iOS actualmente inactivo.

- La línea 12 tiene un subrayado ondulado de color rojo en el identificador `BYE` porque este identificador no está definido en el proyecto activo.

## <a name="intellisense-for-stand-alone-files"></a>IntelliSense para archivos independientes

Al abrir un único archivo fuera de cualquier proyecto, se sigue obteniendo IntelliSense. Puede habilitar o deshabilitar características específicas de IntelliSense en el cuadro de diálogo **Opciones**, en **Editor de texto** > **C/C++**  > **Avanzado**. Para configurar IntelliSense para archivos individuales que no forman parte de un proyecto, busque la sección **IntelliSense y exploración para archivos que no forman parte de proyectos**.

![Archivo único de IntelliSense de Visual C&#43;&#43;](../ide/media/vs2015_cpp_single_file_intellisense.png)

De forma predeterminada, IntelliSense de archivo único solo utiliza directorios de inclusión estándar para buscar archivos de encabezado. Para agregar directorios adicionales, abra el menú contextual del nodo **Solución** y agregue el directorio a la lista **Depurar código fuente**, tal como se muestra en la siguiente ilustración:

![Agregar una ruta a un archivo de encabezado.](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>Habilitar o deshabilitar características

Dado que cada persona puede tener una idea diferente de lo que es práctico, casi todas las características de IntelliSense pueden habilitarse o deshabilitarse en el cuadro de diálogo **Opciones**, bajo **Editor de texto** > **C/C++**  > **Avanzado**. El cuadro de diálogo **Opciones** está disponible en el menú **Herramientas** de la barra de menús.

![Cuadro de diálogo Herramientas > Opciones](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>Vea también

- [Usar IntelliSense](../ide/using-intellisense.md)
- [Configurar un proyecto de C++ para IntelliSense](visual-cpp-intellisense-configuration.md)
