---
title: "C&#243;mo crear y aplicar un recurso | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.XamlDesigner.CreateResource"
  - "VS.XamlDesigner.EditResource"
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# C&#243;mo crear y aplicar un recurso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los estilos y las plantillas de elementos del diseñador XAML se almacenan en entidades reutilizables denominadas recursos.  Los estilos permiten establecer las propiedades de los elementos y volver a usar esos valores para lograr una apariencia coherente entre distintos elementos.  Un [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) define la apariencia de un control y además se puede aplicar como un recurso.  Para obtener más información, consulte [Inicio rápido: Aplicar estilos a los controles](http://go.microsoft.com/fwlink/?LinkID=248239) y [Inicio rápido: Plantillas de control](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Siempre que se crea un recurso nuevo a partir de una propiedad, [estilo](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) o `ControlTemplate`, en el cuadro de diálogo **Crear recurso** se puede definir el recurso en el nivel de aplicación, de documento o de elemento.  Estos niveles determinan dónde se puede usar el recurso.  Por ejemplo, si define el recurso en el nivel de elemento, solo se podrá aplicar el recurso al elemento para el que lo creó.  También puede almacenar el recurso en un diccionario de recursos: un archivo independiente que puede volver a usar en otro proyecto.  
  
### Para crear un recurso nuevo  
  
1.  Con un archivo XAML abierto en el diseñador XAML, cree un elemento o elija uno en la ventana Esquema del documento.  
  
2.  En la ventana Propiedades, elija el marcador de propiedad \(aparece como un símbolo de cuadro a la derecha de un valor de propiedad\) y después elija **Convertir en nuevo recurso**.  Un símbolo de cuadro blanco indica un valor predeterminado y un símbolo de cuadro negro indica normalmente que se ha aplicado un recurso local.  
  
     Aparece el cuadro de diálogo correspondiente para crear un recurso.  Este cuadro de diálogo aparece cuando se crea un recurso de pincel:  
  
     ![Cuadro de diálogo Crear recurso](../designers/media/xaml_create_resource.png "xaml\_create\_resource")  
  
3.  En el cuadro **Nombre \(clave\)**, escriba un nombre de clave.  Este es el nombre que puede usar si desea que otros elementos hagan referencia al recurso.  
  
4.  En **Definir en**, elija la opción en la que desea definir el recurso:  
  
    -   Para que el recurso esté disponible en cualquier documento de la aplicación, elija **Aplicación**.  
  
    -   Para que el recurso esté disponible únicamente en el documento actual, elija **Este documento**.  
  
    -   Para que el recurso esté disponible únicamente en el elemento desde el que creó el recurso o en sus elementos secundarios, elija **Este documento** y, en la lista desplegable, seleccione *elemento*: *nombre*.  
  
    -   Para definir el recurso en un archivo de diccionario de recursos que pueda volver a usarse en otros proyectos, haga clic en **Diccionario de recursos** y luego, en la lista desplegable, seleccione un archivo de diccionario de recursos ya existente, por ejemplo, **StandardStyles.xaml**.  
  
5.  Haga clic en el botón **Aceptar** para crear el recurso y aplicarlo al elemento a partir del cual se creó.  
  
### Para aplicar un recurso a un elemento o propiedad  
  
1.  En la ventana Esquema del documento, elija el elemento al que desea aplicar un recurso.  
  
2.  Realice una de las siguientes acciones:  
  
    -   Aplique un recurso a una propiedad.  En la ventana Propiedades, elija el marcador de propiedad al lado del valor de la propiedad, elija **Recurso local** o **Recurso del sistema**, y luego elija un recurso de los disponibles en la lista que aparece.  
  
         Si no ve un recurso que espera ver, es posible que el tipo de ese recurso no coincida con el tipo de la propiedad.  
  
    -   Aplique un recurso de plantilla de control o estilo a un control.  Abra el menú contextual de un control en la ventana Esquema del documento, elija **Editar plantilla** o **Editar plantillas adicionales**, elija **Aplicar recurso** y, a continuación, elija el nombre de la plantilla de control en la lista que aparece.  
  
        > [!NOTE]
        >  **Editar plantilla** se usa para aplicar plantillas de control.  **Editar plantillas adicionales** se usa para aplicar otros tipos de plantilla.  
  
     Los recursos pueden aplicarse siempre que sean compatibles.  Por ejemplo, un recurso de pincel puede aplicarse a la propiedad **Foreground** de un control <xref:Windows.UI.Xaml.Controls.TextBox>.  
  
### Para editar un recurso  
  
1.  Elija un elemento en la mesa de trabajo o en la ventana Esquema del documento.  
  
2.  En la ventana Propiedades, elija el marcador de propiedad predeterminado o local y, a continuación, elija **Editar recurso** para abrir el cuadro de diálogo **Editar recurso**.  
  
3.  Modifique las opciones del recurso.  
  
## Vea también  
 [Tutorial: Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)