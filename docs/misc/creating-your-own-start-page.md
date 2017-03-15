---
title: "Crear su propia p&#225;gina de inicio | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Crear página de inicio"
  - "página de inicio personalizada"
  - "personalizar página de inicio"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Crear su propia p&#225;gina de inicio
Puede crear una página de inicio personalizada con la plantilla de proyecto de página de inicio o mediante la creación de una página de inicio en blanco.  
  
 Es posible que el diseñador XAML no ofrezca representaciones visuales completamente precisas de las páginas de inicio personalizadas, debido a las dependencias en el modelo de aplicaciones de Visual Studio.  
  
## Usar la plantilla de proyecto  
 La plantilla de proyecto de página de inicio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio. Luego, puede editar la página de inicio según sus especificaciones.  
  
#### Para crear una página de inicio personalizada mediante la plantilla de proyecto de página de inicio  
  
1.  Descargue e instale la [plantilla de proyecto de página de inicio](http://go.microsoft.com/fwlink/?LinkId=186204) desde la Galería de Visual Studio.  
  
    > [!WARNING]
    >  En este momento no se ha actualizado la plantilla de proyecto de página de inicio de Visual Studio 2010. Para obtener información sobre cómo actualizar esta plantilla, vea [Cómo: Actualizar una página de inicio personalizada de Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
2.  Después de haber instalado la plantilla, cree un nuevo proyecto de página de inicio con ella.  
  
3.  En el panel izquierdo del cuadro de diálogo Nuevo proyecto, en **Plantillas instaladas**, expanda el nodo **Otros tipos de proyectos** y después haga clic en **Extensibilidad**.  
  
4.  En el panel central, haga clic en **Página de inicio personalizada**, asigne un nombre al proyecto y haga clic en **Aceptar**.  
  
     Visual Studio crea un proyecto de página de inicio que es una copia completa de la página de inicio de Visual Studio.  
  
5.  En el **Explorador de soluciones**, abra el archivo **StartPage.xaml**.  
  
6.  Edite StartPage.xaml.  
  
     Puede ver su trabajo si presiona F5, que abrirá una instancia experimental de Visual Studio con la página de inicio personalizada instalada.  
  
## Crear una página de inicio en blanco  
 La manera más fácil de crear una página de inicio en blanco es utilizar la plantilla de proyecto de página de inicio y después quitar el contenido.  
  
#### Para crear una página de inicio en blanco mediante la plantilla de proyecto de página de inicio  
  
1.  Cree un proyecto de página de inicio mediante la plantilla de proyecto de página de inicio, tal y como se describe en el procedimiento anterior.  
  
2.  Abra StartPage.xaml.  
  
3.  Quite todo el contenido de la página, dejando solamente los elementos xml externos y el elemento <xref:System.Windows.Controls.Grid> de cuadrícula contenedora, de forma que el archivo .xaml se parezca al ejemplo siguiente.  
  
     [!code-xml[BlankStartPage#01](../misc/codesnippet/Xaml/creating-your-own-start-page_1.xaml)]  
  
4.  Quite los archivos auxiliares que no pretenda usar.  
  
     Debe mantener los archivos .vsix y .pkgdef para fines de implementación.  
  
 Como alternativa, puede crear una página de inicio en blanco mediante la creación de un archivo XAML con la estructura de etiquetas correcta para que la reconozca Visual Studio. Después, puede agregar marcado y código subyacente para obtener la apariencia y funcionalidad deseadas. Para obtener más información, consulta [Crear una página principal personalizada](../extensibility/creating-a-custom-start-page.md).  
  
## Probar y aplicar la página de inicio personalizada  
 No establezca la instancia principal para ejecutar la página de inicio personalizada hasta que compruebe que no se bloquea. Cuando haya probado su página de inicio personalizada, puede aplicarla al sistema repitiendo los tres últimos pasos de este procedimiento en la instancia principal de Visual Studio.  
  
#### Para probar una página de inicio personalizada  
  
1.  Presione F5.  
  
     La instancia experimental de Visual Studio se abre con la nueva página de inicio instalada, pero sin seleccionar.  
  
2.  En la instancia experimental de Visual Studio, en el menú **Herramientas**, haga clic en **Opciones**.  
  
3.  En el cuadro de diálogo **Opciones**, en **Entorno**, seleccione **Inicio**. Después, en la lista **Personalizar página de inicio**, seleccione el archivo .xaml y haga clic en **Aceptar**.  
  
4.  En el menú **Vista**, haga clic en **Página de inicio**.  
  
     Se muestra la página de inicio en funcionamiento. Debe cerrar la instancia experimental, volver a copiar los archivos modificados y, luego, volver a abrir la instancia experimental para ver los nuevos cambios.  
  
 Puede compartir su página de inicio personalizada si carga el archivo .vsix del directorio bin\\debug en el sitio web de la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) o en otro sitio web o recurso compartido de intranet. Para obtener más información, consulta [Implementar páginas de inicio personalizado](../extensibility/deploying-custom-start-pages.md).  
  
## Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)