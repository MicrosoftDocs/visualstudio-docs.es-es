---
title: Crear su propia página de inicio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create start page
- custom start page
- customize start page
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
manager: douge
ms.openlocfilehash: 87195c318f6bdc04dc0cfde54c35577142661224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566026"
---
# <a name="creating-your-own-start-page"></a>Crear su propia página de inicio
Puede crear una página de inicio personalizada con la plantilla de proyecto de página de inicio o mediante la creación de una página de inicio en blanco.  
  
 Es posible que el diseñador XAML no ofrezca representaciones visuales completamente precisas de las páginas de inicio personalizadas, debido a las dependencias en el modelo de aplicaciones de Visual Studio.  
  
## <a name="using-the-project-template"></a>Usar la plantilla de proyecto  
 La plantilla de proyecto de página de inicio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio. Luego, puede editar la página de inicio según sus especificaciones.  
  
#### <a name="to-create-a-custom-start-page-by-using-the-start-page-project-template"></a>Para crear una página de inicio personalizada mediante la plantilla de proyecto de página de inicio  
  
1.  Descargue e instale la [plantilla de proyecto de página de inicio](http://go.microsoft.com/fwlink/?LinkId=186204) desde la Galería de Visual Studio.  
  
    > [!WARNING]
    >  En este momento no se ha actualizado la plantilla de proyecto de página de inicio de Visual Studio 2010. Para obtener información sobre cómo actualizar esta plantilla, consulte [Cómo: actualizar una página de inicio de Visual Studio personalizado](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Después de haber instalado la plantilla, cree un nuevo proyecto de página de inicio con ella.  
  
3.  En el panel izquierdo del cuadro de diálogo Nuevo proyecto, en **Plantillas instaladas**, expanda el nodo **Otros tipos de proyectos** y después haga clic en **Extensibilidad**.  
  
4.  En el panel central, haga clic en **Página de inicio personalizada**, asigne un nombre al proyecto y haga clic en **Aceptar**.  
  
     Visual Studio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio.  
  
5.  En el **Explorador de soluciones**, abra el archivo **StartPage.xaml**.  
  
6.  Edite StartPage.xaml.  
  
     Puede ver su trabajo si presiona F5, que abrirá una instancia experimental de Visual Studio con la página de inicio personalizada instalada.  
  
## <a name="creating-a-blank-start-page"></a>Crear una página de inicio en blanco  
 La manera más fácil de crear una página de inicio en blanco es utilizar la plantilla de proyecto de página de inicio y después quitar el contenido.  
  
#### <a name="to-create-a-blank-start-page-by-using-the-start-page-project-template"></a>Para crear una página de inicio en blanco mediante la plantilla de proyecto de página de inicio  
  
1.  Cree un proyecto de página de inicio mediante la plantilla de proyecto de página de inicio, tal y como se describe en el procedimiento anterior.  
  
2.  Abra StartPage.xaml.  
  
3.  Quitar todo el contenido de la página, dejando sólo los elementos xml externos y la cuadrícula que contiene <xref:System.Windows.Controls.Grid> elemento, por lo que el archivo .xaml es similar al siguiente.  
  
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
      
4.  Quite los archivos auxiliares que no pretenda usar.  
  
     Debe mantener los archivos .vsix y .pkgdef para fines de implementación.  
  
 Como alternativa, puede crear una página de inicio en blanco mediante la creación de un archivo XAML con la estructura de etiquetas correcta para que la reconozca Visual Studio. Después, puede agregar marcado y código subyacente para obtener la apariencia y funcionalidad deseadas. Para obtener más información, consulte [creación de una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).  
  
## <a name="testing-and-applying-the-custom-start-page"></a>Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea. Cuando haya probado su página de inicio personalizada, puede aplicarla al sistema repitiendo los tres últimos pasos de este procedimiento en la instancia principal de Visual Studio.  
  
#### <a name="to-test-a-custom-start-page"></a>Para probar una página de inicio personalizada  
  
1.  Presione F5.  
  
     La instancia experimental de Visual Studio se abre con la nueva página de inicio instalada, pero sin seleccionar.  
  
2.  En la instancia experimental de Visual Studio, en el menú **Herramientas** , haga clic en **Opciones**.  
  
3.  En el cuadro de diálogo **Opciones** , en **Entorno**, seleccione **Inicio**. Después, en la lista **Personalizar página de inicio** , seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
4.  En el menú **Vista** , haga clic en **Página de inicio**.  
  
     Se muestra la página de inicio en funcionamiento. Debe cerrar la instancia experimental, volver a copiar los archivos modificados y, luego, volver a abrir la instancia experimental para ver los nuevos cambios.  
  
 Puede compartir su página de inicio personalizada si carga el archivo .vsix del directorio bin\debug en el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) o en otro sitio web o recurso compartido de intranet. Para obtener más información, consulte [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Tutorial: adición de XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)