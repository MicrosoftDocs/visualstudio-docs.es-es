---
title: "Paso 2: Agregar un objeto aleatorio y una lista de iconos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Paso 2: Agregar un objeto aleatorio y una lista de iconos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este paso, creará un conjunto de símbolos para formar parejas en el juego.  Cada símbolo se agrega a dos celdas aleatorias del elemento TableLayoutPanel en el formulario.  Para ello, se utilizan dos instrucciones `new` para crear dos objetos.  El primero es un objeto `Random` como el usado en el juego de la prueba de matemáticas.  Se utiliza en este código para elegir aleatoriamente celdas de TableLayoutPanel.  El segundo objeto, que tal vez no conozca, es un objeto `List` que se utiliza para almacenar los símbolos elegidos al azar.  
  
### Para agregar un objeto Random y una lista de iconos  
  
1.  En el **Explorador de soluciones**, elija **Form1.cs** si usa Visual C\# o **Form1.vb** si usa Visual Basic y, en la barra de menús, elija **Ver**, **Código**.  También puede elegir la tecla **F7** o hacer doble clic en **Form1** en el **Explorador de soluciones**.  
  
     Se mostrará el módulo de código subyacente de Form1.  
  
2.  En el código existente, agregue el siguiente código.  
  
     [!code-cs[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]  
  
     Si usa Visual C\#, asegúrese de que coloca el código detrás de la llave de apertura y justo detrás de la declaración de clase \(`public partial class Form1 : Form`\).  Si usa Visual Basic, coloque el código justo detrás de la declaración de clase \(`Public Class Form1`\).  
  
3.  Al agregar el objeto `List`, observe que se abre la ventana **IntelliSense**.  El ejemplo siguiente corresponde a Visual C\#, pero aparece un texto similar cuando se agrega una lista en Visual Basic.  
  
     ![Ventana Propiedades mostrando el evento Click](../ide/media/express_listintellisense.png "Express\_ListIntellisense")  
Ventana IntelliSense  
  
    > [!NOTE]
    >  La ventana de Intellisense solo aparece cuando se escribe código manualmente.  Si copia y pega el código, no aparece.  
  
     Es más sencillo comprender el código \(y los comentarios\) si se examina en secciones pequeñas.  Sus programas pueden utilizar objetos `List` para realizar un seguimiento de muchos tipos de elementos distintos.  Una lista puede contener números, valores true\/false, texto u otros objetos.  Se puede tener un objeto `List` que contiene otros objetos `List`.  Los elementos en una lista se llaman *elementos* y cada lista solo contiene elementos de un tipo.  Por tanto, una lista de números solo puede contener números; no se puede agregar texto a esa lista.  De igual modo, tampoco se pueden agregar números a una lista de valores true\/false.  
  
     Cuando se crea un objeto `List` mediante una instrucción `new`, debe especificar el tipo de datos que desea almacenar en él.  Por eso la información sobre herramientas de la parte superior de la ventana **IntelliSense** muestra los tipos de elementos de la lista.  Además, eso es lo que significa `List<string>` \(en Visual C\#\) y `List(Of String)` \(en Visual Basic\): es un objeto `List` que contiene elementos del tipo de datos `string`.  Una cadena es lo que su programa utiliza para almacenar texto, que es lo que la información sobre herramientas de la parte derecha de la ventana **IntelliSense** le indica.  
  
4.  En Visual Basic se debe crear primero una matriz temporal, pero en Visual C\#, la lista se puede crear con una instrucción.  Esto es así porque el lenguaje Visual C\# tiene *inicializadores de colección*, que preparan la lista para aceptar valores.  En Visual Basic, puede utilizar un inicializador de colección.  Sin embargo, por compatibilidad con la versión anterior de Visual Basic, recomendamos utilizar el código anterior.  
  
     Al utilizar un inicializador de colección con una instrucción `new`, una vez creado el nuevo objeto `List`, el programa lo rellena con los datos que especifique entre las llaves.  En este caso, se obtiene una lista de cadenas denominadas **iconos**; la lista se inicializará para que contenga dieciséis cadenas.  Cada una de esas cadenas es una letra única y todas corresponden a los iconos que se mostrarán en las etiquetas.  Así que el juego tendrá un par de signos de exclamación, un par de letras N en mayúscula, un par de comas, etc. \(Cuando estos caracteres se establezcan en la fuente Webdings, aparecerán en forma de símbolos, como un autobús, una bicicleta, una araña, etc.\). El objeto `List` tendrá dieciséis cadenas en total, una por cada celda del panel TableLayoutPanel.  
  
    > [!NOTE]
    >  En Visual Basic, se obtiene el mismo resultado, pero las cadenas se colocan primero en una matriz temporal, que se convierte después en un objeto `List`.  Una matriz es similar a una lista, salvo que las matrices se crean con un tamaño fijo.  Las listas pueden reducir y crecer según sea necesario, algo que es importante en este programa.  
  
### Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 3: Asignar un icono aleatorio a cada etiqueta](../ide/step-3-assign-a-random-icon-to-each-label.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 1: Crear un proyecto y agregar una tabla a un formulario](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).