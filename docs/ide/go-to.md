---
title: Ir a | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>Ir a
Existen muchas maneras de navegar fácilmente por el código dentro del IDE de Visual Studio, tanto con el teclado como con el mouse.

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>Ir a todo
Esta característica existe en Visual Studio 2017 y versiones posteriores.  Le permite navegar por su código para encontrar los elementos específicos que busca.  Puede buscar una línea, tipo, símbolo o archivo específicos, entre otros, desde una interfaz sencilla y unificada.

### <a name="how-to-use"></a>Cómo se usa
* **Teclado**
  * Presione **Ctrl+,** o **Ctrl+T**.  (Tenga en cuenta que su método abreviado de teclado puede ser diferente en función del perfil que haya seleccionado).
* **Mouse**
  * Seleccione **Editar > Ir a > Ir a todo**.

Esto mostrará una ventana pequeña en la parte superior derecha de su IDE, de manera predeterminada.

![Ir a todo](media/gotoall.png)

Desde aquí, existen varias maneras de continuar:
* Escriba texto sin un prefijo para buscar con los [iconos de filtrado](#filtered-searches) seleccionados debajo del cuadro de texto.
* Escriba un [prefijo](#filtered-searches) seguido del texto que se va a buscar.
* Escriba un signo de interrogación (?) para obtener ayuda adicional.
  ![Ayuda de Ir a todo](media/gotoall_help.png)

### <a name="filtered-searches"></a>Búsquedas filtradas
Para restringir la búsqueda a un tipo específico, puede usar un prefijo al escribir o usar los iconos debajo de la ventana de búsqueda como se muestra a continuación.

Prefijo | Iconos | Acceso directo | Descripción
:----: | ---- | -------- | ---
#      | ![Icono de símbolo](media/gotoall_symbolicon.png) | Ctrl+1, Ctrl+S | Buscar símbolos coincidentes
f      | ![Icono de archivo](media/gotoall_fileicon.png)     | Ctrl+1, Ctrl+F | Buscar nombres de archivo coincidentes
m      | ![Icono de miembro](media/gotoall_membericon.png) | Ctrl+1, Ctrl+M | Buscar miembros coincidentes
m      | ![Icono de tipo](media/gotoall_typeicon.png)     | Ctrl+1, Ctrl+T | Buscar tipos coincidentes
:      | ![Icono de línea](media/gotoall_lineicon.png)     | Ctrl+G         | Ir al número de línea que se ha especificado

### <a name="search-locations"></a>Ubicaciones de búsqueda
Para restringir la búsqueda a ubicaciones específicas, use los dos iconos de documento.

Iconos | Descripción
---- | ---
![Documento actual](media/gotoall_currentdocument.png) | Buscar solo en el documento actual
![Documentos externos](media/gotoall_external.png) | Buscar en documentos externos y en los que se encuentran en el proyecto o solución

### <a name="settings"></a>Configuración
Hacer clic en el icono de engranaje ![Icono de engranaje](media/gotoall_gear.png) en la parte inferior derecha le permite cambiar el funcionamiento de esta característica.

Configuración | Descripción
------- | ---
Usar pestaña de vista previa | Mostrar el elemento seleccionado inmediatamente en la pestaña de vista previa del IDE
Mostrar detalles    | Mostrar la información de resumen, línea, archivo y proyecto de los comentarios de documentación en la ventana
Centrar ventana   | Mover esta ventana al centro del IDE en lugar de a la parte superior derecha
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>Ir a definición
Vaya al origen de un tipo y abra el resultado en una pestaña nueva:

Entrada        | Función 
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **F12**
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ir a definición**

## <a name="peek-definition"></a>Ver la definición
Obtenga una vista previa de la definición de un tipo en una ventana emergente en lugar de en una pestaña nueva:

Entrada        | Función 
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Alt+F12**
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ver la definición**

Si ve otra definición de la ventana emergente, iniciará una ruta de navegación en la que puede desplazarse con los círculos y las flechas que aparecen encima de la ventana emergente.  Para obtener más información, vea [Cómo: Ver y editar código mediante Definición de Peek (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="go-to-implementation"></a>Ir a implementación
Navegue desde una clase base o escriba sus implementaciones.  Si existen varias implementaciones, las verá en la ventana **Resultados de la búsqueda de símbolos**:

Entrada        | Función 
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Ctrl+F12**
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Ir a implementación**

## <a name="find-all-references"></a>Buscar todas las referencias
Buscar todos los lugares en los que se usa un método, propiedad o variable.  Puede usar esto para comprobar un código no alcanzado y los posibles efectos secundarios de una refactorización grande.  Presione **F8** para desplazarse entre los resultados.

Entrada        | Función 
------------ | ---
**Teclado** | Coloque el cursor de texto en algún lugar del nombre de tipo y presione **Ctrl+K, R**
**Mouse**    | Haga clic con el botón derecho en el nombre de tipo y seleccione **Buscar todas las referencias**

## <a name="navigating-results"></a>Navegar por los resultados
Al usar las características de navegación en Visual Studio, puede desplazarse hacia delante y hacia atrás en la pila:

Entrada        | Función 
------------ | ---
**Ctrl+-**          | Navegar hacia atrás en la pila
**Ctrl+Mayús+-**    | Navegar hacia delante en la pila

También puede usar los elementos de menú **Ver > Navegar hacia atrás** y **Ver > Navegar hacia delante**.
