---
title: "Generación de un constructor: generación de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>Generación de un constructor en C# #
**Qué:** Le permite generar el código de inmediato para un nuevo constructor en una clase. 

**Cuándo:** Introduce un nuevo constructor y desea declararlo adecuadamente de manera automática, o modifica un constructor existente. 

**Por qué:** Podría declarar el constructor antes de usarlo; sin embargo, esta característica lo generará, con los parámetros adecuados, automáticamente. Además, la modificación de un constructor existente requiere la actualización de todos los sitios de llamada, a menos que utilice esta característica para actualizarlos automáticamente.

**Cómo:** Hay varias maneras de generar un constructor:
- [Generación de constructor y selección de miembros](#pick)
- [Generación de constructor a partir de campos seleccionados](#selection)
- [Generación de constructor a partir de nuevo uso](#usage)
- [Adición de parámetro a constructor existente](#addparameter)
- [Creación e inicialización de campo/propiedad a partir de un parámetro de constructor](#create)

## <a id = "pick"></a> Generación de constructor y selección de miembros
1. Coloque el cursor en cualquier línea vacía de una clase:

   ![Cursor en una línea vacía](media/constructor1-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Generar constructor...** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Generar constructor...** en el menú emergente de la ventana Vista previa.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea vacía de la clase.

   ![Vista previa de generación de constructor](media/constructor1-preview-cs.png)

1. Aparecerá un cuadro de diálogo que le permite seleccionar y elegir los miembros que desea utilizar como parámetros de constructor, así como ordenarlos (con las flechas arriba y abajo). Presione **Aceptar** para confirmar los cambios
  
   ![Cuando de diálogo Selección de miembros](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >Puede activar la casilla **Agregar comprobaciones de valores null** para generar automáticamente comprobaciones de valores null para los parámetros de constructor.

1. El constructor se creará con los parámetros seleccionados en el orden especificado.
   ![Resultado de la generación de constructor](media/constructor1-result-cs.png)

## <a id="selection"></a> Generación de constructor a partir de campos seleccionados
1. Destaque los miembros que desea tener en su constructor generado: ![Destacar miembros](media/constructor2-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Generar constructor "NombreTipo(...)"** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Generar constructor "NombreTipo(...)"** en el menú emergente de la ventana Vista previa.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con la selección.

     ![Vista previa de generación de constructor](media/constructor2-preview-cs.png)

1. El constructor se creará con los parámetros seleccionados.
     ![Resultado de la generación de constructor](media/constructor2-result-cs.png)

## <a id="usage"></a> Generación de constructor a partir de nuevo uso
1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un constructor que aún no existe.

   ![Código resaltado](media/constructor-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Generar constructor en "*NombreTipo*"** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Generar constructor en "*NombreTipo*"** en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

   ![Vista previa de generación de constructor](media/constructor-preview-cs.png)

   >[!TIP]
   >Use el vínculo [**Vista previa de los cambios**](../../ide/preview-changes.md) en la parte inferior de la ventana de vista previa para ver todos los cambios que se aplicarán antes de hacer la selección.

1. El constructor se creará automáticamente con los parámetros que se deducen de su uso.

   ![Resultado de la generación de constructor](media/constructor-result-cs.png)

## <a id="addparameter"></a> Adición de parámetro a constructor existente
1. Agregue un parámetro a una instancia de objeto existente.

1. Coloque el cursor en la línea donde hay un subrayado ondulado de color rojo que indica que ha utilizado un constructor que aún no existe.
    
    ![Destacado de generación de constructor](media/constructor4-highlight-cs.png)

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Agregar parámetro a "NombreTipo(...)"** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Agregar parámetro a "NombreTipo(...)"** en el menú emergente de la ventana Vista previa.
     * Mantenga el mouse sobre el subrayado ondulado de color rojo y haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el subrayado ondulado de color rojo.

    ![Vista previa de generación de constructor](media/constructor4-preview-cs.png)

1. El parámetro se agregará automáticamente con su tipo inferido a partir de su uso.
   
   ![Resultado de la generación de constructor](media/constructor4-result-cs.png)

## <a id="create"></a> Creación e inicialización de campo/propiedad a partir de un parámetro de constructor
1. A partir de un constructor existente, agregue un parámetro:

   ![Destacado de generación de constructor](media/constructor5-highlight-cs.png)

1. Coloque el cursor dentro del parámetro recién agregado.

1. A continuación, realice alguno de los siguientes procedimientos:
   * **Teclado**
     * Presione **Ctrl +.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Crear e inicializar propiedad "SuPropiedad"** o **Crear e inicializar campo "SuCampo"** en el menú emergente de la ventana Vista previa.
   * **Mouse**
     * Haga clic con el botón derecho y seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Crear e inicializar propiedad "SuPropiedad"** o **Crear e inicializar campo "SuCampo"** en el menú emergente de la ventana Vista previa.
     * Haga clic en el botón ![de icono Bombilla](media/bulb-cs.png) que aparece en el margen izquierdo si el cursor de texto ya está en la línea con el parámetro agregado.

   ![Vista previa de generación de constructor](media/constructor5-preview-cs.png)

1. Se creará el campo o la propiedad y se le pondrá un nombre que coincida con sus tipos.

   ![Resultado de la generación de constructor](media/constructor5-result-cs.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)  
[Vista previa de cambios](../../ide/preview-changes.md)