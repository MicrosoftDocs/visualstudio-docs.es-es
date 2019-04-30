---
title: Cómo crear y aplicar un recurso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 47c7385ba54e432e42575f5b8cbae29172ddf62b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434472"
---
# <a name="how-to-create-and-apply-a-resource"></a>Cómo crear y aplicar un recurso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los estilos y las plantillas de elementos del diseñador XAML se almacenan en entidades reutilizables denominadas recursos. Los estilos permiten establecer las propiedades de los elementos y volver a usar esos valores para lograr una apariencia coherente entre distintos elementos. Una propiedad [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) define la apariencia de un control y también puede aplicarse como un recurso. Para obtener más información, vea [Inicio rápido: diseñar controles](http://go.microsoft.com/fwlink/?LinkID=248239) e [Inicio rápido: plantillas de control](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Siempre que crea un recurso a partir de una propiedad existente, [Style](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) o `ControlTemplate`, el cuadro de diálogo **Crear recurso** permite definir el recurso en el nivel de aplicación, nivel de documento o nivel de elemento. Estos niveles determinan dónde se puede usar el recurso. Por ejemplo, si define el recurso en el nivel de elemento, solo se podrá aplicar el recurso al elemento para el que lo creó. También puede almacenar el recurso en un diccionario de recursos: un archivo independiente que puede volver a usar en otro proyecto.  
  
### <a name="to-create-a-new-resource"></a>Para crear un recurso nuevo  
  
1. Con un archivo XAML abierto en el diseñador XAML, cree un elemento o elija uno en la ventana Esquema del documento.  
  
2. En la ventana Propiedades, seleccione el marcador de propiedad (aparece como un símbolo de cuadro a la derecha de un valor de propiedad) y, después, pulse **Convertir en nuevo recurso**. Un símbolo de cuadro blanco indica un valor predeterminado y un símbolo de cuadro negro indica normalmente que se ha aplicado un recurso local.  
  
     Aparece el cuadro de diálogo correspondiente para crear un recurso. Este cuadro de diálogo aparece cuando se crea un recurso de pincel:  
  
     ![Cuadro de diálogo Crear recurso](../designers/media/xaml-create-resource.png "xaml_create_resource")  
  
3. En el cuadro **Nombre (clave)**, escriba un nombre de clave. Este es el nombre que puede usar si desea que otros elementos hagan referencia al recurso.  
  
4. En **Definir en**, seleccione la opción en la que quiere definir el recurso:  
  
    - Para que el recurso esté disponible en cualquier documento de la aplicación, seleccione **Aplicación**.  
  
    - Para que el recurso esté disponible únicamente en el documento actual, seleccione **Este documento**.  
  
    - Para que el recurso esté disponible únicamente en el elemento desde el que creó el recurso o en sus elementos secundarios, seleccione **Este documento** y, en la lista desplegable, seleccione *elemento*: *nombre*.  
  
    - Para definir el recurso en un archivo de diccionario de recursos que pueda volver a usarse en otros proyectos, haga clic en **Diccionario de recursos** y luego, en la lista desplegable, seleccione un archivo de diccionario de recursos ya existente, por ejemplo, **StandardStyles.xaml**.  
  
5. Haga clic en el botón **Aceptar** para crear el recurso y aplicarlo al elemento a partir del cual se ha creado.  
  
### <a name="to-apply-a-resource-to-an-element-or-property"></a>Para aplicar un recurso a un elemento o propiedad  
  
1. En la ventana Esquema del documento, elija el elemento al que desea aplicar un recurso.  
  
2. Realice una de las siguientes acciones:  
  
   - Aplique un recurso a una propiedad. En la ventana Propiedades, seleccione el marcador de propiedad al lado del valor de la propiedad, seleccione **Recurso local** o **Recurso del sistema**, y luego seleccione un recurso de los disponibles en la lista que aparece.  
  
      Si no ves un recurso que esperabas ver, es posible que sea porque el tipo del recurso no coincide con el tipo de la propiedad.  
  
   - Aplique un recurso de plantilla de control o estilo a un control. Abra el menú contextual de un control en la ventana Esquema del documento, seleccione **Editar plantilla** o **Editar plantillas adicionales**, seleccione **Aplicar recurso** y, después, seleccione el nombre de la plantilla de control en la lista que aparece.  
  
     > [!NOTE]
     > **Editar plantilla** se usa para aplicar plantillas de control. **Editar plantillas adicionales** se usa para aplicar otros tipos de plantilla.  
  
     Los recursos pueden aplicarse siempre que sean compatibles. Por ejemplo, un recurso de pincel puede aplicarse a la propiedad **Foreground** de un control <xref:Windows.UI.Xaml.Controls.TextBox>.  
  
### <a name="to-edit-a-resource"></a>Para editar un recurso  
  
1. Elija un elemento en la mesa de trabajo o en la ventana Esquema del documento.  
  
2. En la ventana Propiedades, seleccione el marcador de propiedad predeterminado o local y, después, seleccione **Editar recurso** para abrir el cuadro de diálogo **Editar recurso**.  
  
3. Modifique las opciones del recurso.  
  
## <a name="see-also"></a>Vea también  
 [Crear una UI usando el Diseñador XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
