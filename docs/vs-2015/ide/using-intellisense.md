---
title: Usar IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5cc5efe7dd32fe5953012594a5bb5fce49f947d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574235"
---
# <a name="using-intellisense"></a>Using IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense).  
  
IntelliSense es el término general que se usa para describir varias características: Lista de miembros, Información de parámetros, Información rápida y Palabra completa. Estas características le permiten obtener más información acerca del código que utiliza, a realizar un seguimiento de los parámetros que escribe y a agregar llamadas a propiedades y a métodos con tan solo presionar unas teclas.  
  
 Muchos aspectos de IntelliSense son específicos del lenguaje. Para obtener más información acerca de IntelliSense para los distintos lenguajes, consulte los temas que se muestran en Vea también.  
  
## <a name="list-members"></a>Lista de miembros  
 Después de escribir un carácter desencadenador (por ejemplo, un punto (`.`) en código administrado o `::` en C++), aparece una lista de los miembros válidos de un tipo (o espacio de nombres). Si sigue escribiendo caracteres, la lista se filtra para incluir solo los miembros que comienzan por esos caracteres.  
  
 Después de seleccionar un elemento, puede insertarlo en el código presionando la tecla TAB o escribiendo un espacio. Si selecciona un elemento y escribe un punto, el elemento aparece seguido del punto, con lo que se muestra otra lista de miembros. Cuando seleccione un elemento, obtendrá la información rápida del mismo antes de insertarlo.  
  
 En la lista de miembros, el icono de la izquierda representa el tipo del miembro, como el espacio de nombres, la clase, la función o la variable. Para ver una lista de iconos, vea [Iconos de la vista de clases y del examinador de objetos](../ide/class-view-and-object-browser-icons.md). La lista puede ser bastante larga, por lo que puede presionar RE PÁG o AV PÁG para subir o bajar en ella.  
  
 ![Lista de miembros de Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")  
  
 Puede invocar la característica **Lista de miembros** manualmente. Para ello, presione CTRL+J y haga clic en **Editar/IntelliSense/Lista de miembros** o en el botón **Lista de miembros** de la barra de herramientas del editor. Cuando se invoca en una línea en blanco o fuera de un ámbito reconocible, la lista muestra símbolos del espacio de nombres global.  
  
 Para desactivar la lista de miembros de forma predeterminada (de manera que no aparezca a menos que se invoque específicamente), vaya a **Herramientas/Opciones/Todos los lenguajes** y anule la selección de **Lista de miembros automática**. Si quiere desactivar la lista de miembros únicamente para un lenguaje concreto, vaya a la configuración **General** de ese lenguaje.  
  
 También puede cambiar al modo de sugerencias, en el que solo se inserta en el código el texto que se escribe. Por ejemplo, si escribe en un identificador que no está en la lista y presiona la tecla TAB en modo de finalización, la entrada reemplaza al identificador escrito. Para alternar entre el modo de finalización y el modo de sugerencias, presione CTRL+ALT+BARRA ESPACIADORA o haga clic en **Editar/IntelliSense/Alternar el modo de finalización**.  
  
## <a name="parameter-info"></a>Información de parámetros  
 La información de parámetros proporciona información acerca del número, los nombres y los tipos de parámetros que requiere un método, un parámetro de tipo genérico de atributo (en C#) o una plantilla (en C++).  
  
 El parámetro en negrita indica el siguiente parámetro requerido a medida que escribe la función. En el caso de funciones sobrecargadas, se puede utilizar las teclas de flecha ARRIBA y ABAJO para ver información de parámetros alternativos para las sobrecargas de funciones.  
  
 ![Información de parámetros](../ide/media/vs2015-param-info.png "VS2015_param_Info")  
  
 Cuando se anotan funciones y parámetros con comentarios de documentación XML, los comentarios se muestran como Información de parámetros. Para obtener más información, vea [Proporcionar comentarios del código XML](../ide/supplying-xml-code-comments.md).  
  
 Para invocar manualmente la información de parámetros, haga clic en **Editar/IntelliSense/Información de parámetros**, presione CTRL+MAYÚS+BARRA ESPACIADORA o haga clic en el botón **Información de parámetros** de la barra de herramientas del editor.  
  
## <a name="quick-info"></a>Información rápida  
 La opción Información rápida muestra la declaración completa de cualquier identificador del código.  
  
 ![Información rápida de Visual Studio](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")  
  
 Cuando se selecciona un miembro en el cuadro **Lista de miembros**, también aparece la información rápida.  
  
 ![Información de parámetros en un archivo de código de C&#35;](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")  
  
 Para invocar manualmente la información rápida, haga clic en **Editar/IntelliSense/Información rápida**, presione CTRL+I o haga clic en el botón **Información rápida** de la barra de herramientas del editor.  
  
 Si una función está sobrecargada, es posible que IntelliSense no muestre información para todas las formas de la sobrecarga.  
  
 Puede desactivar la información rápida en C++ estableciendo **Herramientas/Opciones/Editor de texto/C/C++/Avanzadas/Información rápida automática** en `false`.  
  
## <a name="complete-word"></a>Palabra completa  
 La opción Palabra completa escribe el resto del nombre de una variable, un comando o una función una vez que ha escrito suficientes caracteres como para reconocerlo. Para invocar Palabra completa, haga clic en **Editar/IntelliSense/Palabra completa**, presione CTRL+ESPACIO o haga clic en el botón **Palabra completa** de la barra de herramientas del editor.  
  
## <a name="intellisense-options"></a>Opciones de IntelliSense  
 Las opciones de IntelliSense están activadas de forma predeterminada. Para desactivarlas, haga clic en **Herramientas/Opciones/Editor de texto** y anule la selección de **Información de parámetros** o de **Lista de miembros automática** si no quiere usar la característica Lista de miembros.  
  
## <a name="troubleshooting-intellisense"></a>Solución de problemas de IntelliSense  
 En algunos casos, es posible que las opciones de IntelliSense no funcionen como esperaba.  
  
 **El cursor está debajo de un error de código.** Quizá no pueda usar IntelliSense si existe una función incompleta u otro error en el código encima del cursor, ya que IntelliSense no puede analizar los elementos del código. Puede resolver este problema marcando como comentario el código correspondiente.  
  
 **El cursor está en un comentario de código.** No puede usar IntelliSense si el cursor está en un comentario del archivo de código fuente.  
  
 **El cursor está en un literal de cadena.** No puede usar IntelliSense si el cursor está en las comillas de un literal de cadena, como en el siguiente ejemplo:  
  
```  
MessageBox( hWnd, "String literal|") )  
```  
  
 **Las opciones automáticas están desactivadas.** De forma predeterminada, IntelliSense funciona automáticamente, pero puede deshabilitarlo. También puede invocar una característica IntelliSense incluso cuando la finalización de instrucciones automática se encuentre deshabilitada.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de IntelliSense específicas de Visual Basic](../ide/visual-basic-specific-intellisense.md)   
 [IntelliSense para Visual C#](../ide/visual-csharp-intellisense.md)   
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)   
 [Proporcionar comentarios del código XML](../ide/supplying-xml-code-comments.md)



