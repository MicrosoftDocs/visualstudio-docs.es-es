---
title: 'Cómo: marcar controles como controles seguros | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016264"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>Cómo: marcar controles como controles seguros
  Por seguridad, SharePoint diferencia entre los controles Web que están protegidos contra la inyección de scripts y los controles Web que no lo son. Los usuarios que no son de confianza pueden tener acceso a los controles protegidos o a *controles seguros*. Puede marcar los controles como seguros en la propiedad entradas de control seguras de un elemento de proyecto de SharePoint o en el **Diseñador de paquetes** al agregar un ensamblado al paquete. Para obtener más información, vea

- [web.config configuración del archivo cambia](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) y [registra un ensamblado de elemento Web como un control seguro](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11)).

> [!IMPORTANT]
> Estos procedimientos son para fines ilustrativos. Marque controles como seguros solo si está seguro de que son seguros.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Marcar controles seguros en la propiedad Safe control entries

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>Para marcar los controles como seguros o no seguros en la propiedad entradas de control seguras

1. Cree una solución de SharePoint con un proyecto de elemento Web visual.

2. Agregue dos controles al elemento Web: un cuadro de texto y un botón. Deje los nombres con sus valores predeterminados, TextBox1 y Button1, respectivamente.

3. Agregue dos entradas a la propiedad de **entradas de control Safe** del elemento Web. Para ello, elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) situado junto a la propiedad **Safe control entries** en la ventana **propiedades** .

     Aparece el cuadro de diálogo **entradas de control seguras** .

4. En el cuadro de diálogo **entradas de control seguras** , elija el botón **Agregar** dos veces para agregar dos entradas de control seguras al panel **miembros** : una para el botón y otra para el cuadro de texto.

5. Elija la primera entrada de control segura y, a continuación, cambie el valor de su propiedad **Safe** a **false**, su propiedad **nombre de tipo** a **button1**y su propiedad **Safe Against script** a **false**.

     Este paso identifica el control de botón como control no seguro.

6. Elija la segunda entrada de control segura en la lista. Deje el valor de la propiedad **Safe** como **true** y establezca su propiedad **nombre de tipo** en **textBox1** y su propiedad **Safe Against script** en **true**.

     El control de cuadro de texto ahora está marcado como control seguro contra la inyección de scripts.

7. Elija el botón **Aceptar** para cerrar el cuadro de diálogo.

## <a name="marking-safe-controls-in-the-package-designer"></a>Marcar controles seguros en el diseñador de paquetes

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>Para marcar los controles como seguros o no seguros en el diseñador de paquetes

1. Cree una solución de SharePoint con un proyecto de elemento Web visual.

2. Agregue dos controles al elemento Web: un cuadro de texto y un botón. Deje los nombres con sus valores predeterminados, TextBox1 y Button1, respectivamente.

     Tome nota del espacio de nombres del control porque se usa más adelante.

3. En la barra de menús, **Elija compilar compilar**  >  **solución** para compilar el proyecto.

4. Cree otra solución de SharePoint.

5. En **Explorador de soluciones**, abra el menú contextual del archivo *Package. Package* y, a continuación, elija **abrir** para abrir el **Diseñador de paquetes**.

6. En el **Diseñador de paquetes**, elija la pestaña **Opciones avanzadas** .

7. En **ensamblados adicionales**, elija el botón **Agregar** y, a continuación, elija **Agregar ensamblado existente** en la lista.

8. En el cuadro de diálogo **Agregar ensamblado existente** , elija el botón de puntos suspensivos (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")) situado junto a **ruta de acceso de origen**.

9. Elija el ensamblado de la solución de SharePoint que creó en el paso 1 y, a continuación, elija el botón **abrir** .

10. En este ejemplo, deje la opción **destino de implementación** como GlobalAssemblyCache.

     Este paso hace que el ensamblado se implemente en la caché de ensamblados global (GAC) del sistema. Si desea que el ensamblado se implemente en la carpeta de aplicación web (bin), seleccione esa opción en su lugar. Para obtener más información, vea [implementar elementos Web en SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

11. En el cuadro **controles seguros** , elija el botón **haga clic aquí para agregar un nuevo elemento** .

12. Escriba los valores de las propiedades de la tabla siguiente.

    |Nombre de propiedad|Value|
    |-------------------|-----------|
    |Espacio de nombres|Espacio de nombres completo para el control, como **BdcModelProject1. VisualWebPart1**.|
    |Nombre del tipo|Button1|
    |Nombre del ensamblado|Un nombre de ensamblado seguro, como: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Seguro|Desactive la casilla **seguro** .|
    |Safe con script|Deje desactivada la casilla **seguro contra scripts** .|

    > [!NOTE]
    > El valor de **nombre de ensamblado** de los ensamblados agregados a través de la pestaña **avanzadas** del **Diseñador de paquetes** no puede ser un token, debe ser un ensamblado con nombre seguro. Para obtener más información, vea [Crear y utilizar ensamblados con nombre seguro](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100)).

13. Elija la tecla **Tab** para crear otra entrada de control segura.

14. Elija el botón **haga clic aquí para agregar un nuevo elemento** .

15. Escriba los valores de las propiedades de la tabla siguiente.

    |Nombre de propiedad|Value|
    |-------------------|-----------|
    |Espacio de nombres|Espacio de nombres completo para el control, como **BdcModelProject1. VisualWebPart1**.|
    |Nombre del tipo|TextBox1|
    |Nombre del ensamblado|Un nombre de ensamblado seguro, como: Microsoft. Office. SharePoint. ClientExtensions, Version = 14.0.0.0, Culture = neutral, PublicKeyToken = 71e9bce111e9429c.|
    |Seguro|Active la casilla **seguro** .|
    |Safe con script|Active la casilla **seguro contra scripts** .|

16. Elija la tecla **Tab** y, a continuación, elija el botón **Aceptar** para cerrar el cuadro de diálogo.

## <a name="see-also"></a>Consulte también
- [Proporcionar información de empaquetado e implementación en los elementos de proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
