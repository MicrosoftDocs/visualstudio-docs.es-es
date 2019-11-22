---
title: Creating Your Own Start Page | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: jillfra
ms.openlocfilehash: ceb78d3310f37a58850199b11fb2b2fed86f6799
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299322"
---
# <a name="creating-your-own-start-page"></a>Crear su propia página de inicio
Puede crear una página de inicio personalizada con la plantilla de proyecto de página de inicio o mediante la creación de una página de inicio en blanco.  
  
 Es posible que el diseñador XAML no ofrezca representaciones visuales completamente precisas de las páginas de inicio personalizadas, debido a las dependencias en el modelo de aplicaciones de Visual Studio.  
  
## <a name="using-the-project-template"></a>Usar la plantilla de proyecto  
 La plantilla de proyecto de página de inicio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio. Luego, puede editar la página de inicio según sus especificaciones.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Para crear una página de inicio personalizada mediante la plantilla de proyecto de página de inicio  
  
1. Descargue e instale la [plantilla de proyecto de página de inicio](https://go.microsoft.com/fwlink/?LinkId=186204) desde la Galería de Visual Studio.  
  
    > [!WARNING]
    > En este momento no se ha actualizado la plantilla de proyecto de página de inicio de Visual Studio 2010. For information about how to upgrade this template, see [How to: Upgrade a Visual Studio Custom Start Page](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2. Después de haber instalado la plantilla, cree un nuevo proyecto de página de inicio con ella.  
  
3. En el panel izquierdo del cuadro de diálogo Nuevo proyecto, en **Plantillas instaladas**, expanda el nodo **Otros tipos de proyectos** y después haga clic en **Extensibilidad**.  
  
4. En el panel central, haga clic en **Página de inicio personalizada**, asigne un nombre al proyecto y haga clic en **Aceptar**.  
  
     Visual Studio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio.  
  
5. En el **Explorador de soluciones**, abra el archivo **StartPage.xaml**.  
  
6. Edite StartPage.xaml.  
  
     Puede ver su trabajo si presiona F5, que abrirá una instancia experimental de Visual Studio con la página de inicio personalizada instalada.  
  
## <a name="creating-a-blank-start-page"></a>Crear una página de inicio en blanco  
 La manera más fácil de crear una página de inicio en blanco es utilizar la plantilla de proyecto de página de inicio y después quitar el contenido.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Para crear una página de inicio en blanco mediante la plantilla de proyecto de página de inicio  
  
1. Cree un proyecto de página de inicio mediante la plantilla de proyecto de página de inicio, tal y como se describe en el procedimiento anterior.  
  
2. Abra StartPage.xaml.  
  
3. Quite todo el contenido de la página, dejando solamente los elementos xml externos y el elemento <xref:System.Windows.Controls.Grid> de cuadrícula contenedora, de forma que el archivo .xaml se parezca al ejemplo siguiente.  
  
   ```xaml
      <Grid xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" 
                xmlns:d="http://schemas.microsoft.com/expression/blend/2008" 
                xmlns:sp="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.StartPage"
                xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.10.0"
                xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.10.0"
            mc:Ignorable="d" 
                d:DesignHeight="600" d:DesignWidth="800">
       <Grid>
           <!--Add content here.-->
       </Grid>
   </Grid>
   ```
      
4. Quite los archivos auxiliares que no pretenda usar.  
  
    Debe mantener los archivos .vsix y .pkgdef para fines de implementación.  
  
   Como alternativa, puede crear una página de inicio en blanco mediante la creación de un archivo XAML con la estructura de etiquetas correcta para que la reconozca Visual Studio. Después, puede agregar marcado y código subyacente para obtener la apariencia y funcionalidad deseadas. For more information, see [Creating a Custom Start Page](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea. Cuando haya probado su página de inicio personalizada, puede aplicarla al sistema repitiendo los tres últimos pasos de este procedimiento en la instancia principal de Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Para probar una página de inicio personalizada  
  
1. Presione F5.  
  
    La instancia experimental de Visual Studio se abre con la nueva página de inicio instalada, pero sin seleccionar.  
  
2. En la instancia experimental de Visual Studio, en el menú **Herramientas** , haga clic en **Opciones**.  
  
3. En el cuadro de diálogo **Opciones** , en **Entorno**, seleccione **Inicio**. Después, en la lista **Personalizar página de inicio** , seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
4. En el menú **Vista** , haga clic en **Página de inicio**.  
  
    Se muestra la página de inicio en funcionamiento. Debe cerrar la instancia experimental, volver a copiar los archivos modificados y, luego, volver a abrir la instancia experimental para ver los nuevos cambios.  
  
   You can share your custom Start Page by uploading the .vsix file from your bin\debug directory to the [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Web site, or to another Web site or intranet share. Para obtener más información, consulta [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Customizing the Start Page](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Tutorial: adición de XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)