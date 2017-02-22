---
title: "Modificar el estilo de objetos en Blend | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Modificar el estilo de objetos en Blend
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La manera más fácil de personalizar un objeto es establecer propiedades en el panel **Propiedades**.  
  
 Si desea volver a utilizar la configuración o un conjunto de configuraciones, cree un recurso reutilizable.  Podría tratarse de un *estilo*, una *plantilla* o algo simple como un color personalizado.  También puede hacer la apariencia de un control sea distinta en función de su estado.  Por ejemplo, que un botón se vuelva verde cuando el usuario haga clic en él.  
  
 **En este tema**:  
  
-   [Pinceles: modificar la apariencia de un objeto](#Brushes)  
  
-   [Estilos y plantillas: crear una apariencia coherente en todos los controles](#Styles)  
  
-   [Estados visuales: cambiar la apariencia de un control según su estado](#Visual)  
  
-   [Recursos: crear colores, estilos y plantillas y volver a usarlos más adelante](#Resources)  
  
##  <a name="Brushes"></a> Pinceles: modificar la apariencia de un objeto  
 Aplique un pincel a un objeto si desea cambiar su apariencia.  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Brushes Editor](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### Pintar una imagen o patrón repetitivos en un objeto  
 Pinte una imagen o patrón repetitivos en un objeto con un *pincel de diseño en mosaico*.  
  
 Para crear un pincel de diseño en mosaico, empiece por crear un recurso de *pincel de imagen*, *pincel con dibujo* o *pincel visual*.  
  
 Cree un pincel de imagen con una imagen.  Las ilustraciones siguientes muestran el pincel de imagen, el pincel de imagen en mosaico y el pincel de imagen volteado.  
  
 Cree un pincel con dibujo mediante un dibujo vectorial como un trazado o forma.  Las ilustraciones siguientes muestran el pincel con dibujo, el pincel con dibujo en mosaico y el pincel con dibujo volteado.  
  
 Cree un pincel visual a partir de un control como un botón.  Las ilustraciones siguientes muestran el pincel visual y el pincel visual en mosaico.  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Tile Brushes](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Estilos y plantillas: crear una apariencia coherente en todos los controles  
 Puede diseñar la apariencia y el comportamiento de un control una vez y aplicar ese diseño a otros controles para no tener que hacerlo de forma individual.  
  
 **¿Debe usar un estilo?** Si desea establecer las propiedades predeterminadas \(como el color de un botón\), utilice un *estilo*.  Puede modificar un control incluso después de aplicarle un estilo.  
  
 **¿Debe usar una plantilla?** Si desea cambiar la estructura de un control, utilice una *plantilla*.  Imagine que convierte un gráfico o un logotipo en un botón.  El control no se puede modificar después de aplicarle una plantilla.  
  
### Crear una plantilla o un estilo  
 Hay dos maneras de crear una plantilla:  puede convertir cualquier objeto de la mesa de trabajo en un control o puede basar la plantilla en un control existente.  
  
 Para convertir cualquier objeto en una plantilla de control, seleccione el objeto y, a continuación, en el menú **Herramientas**, elija **Crear en control**.  
  
 Si desea basar la plantilla en un control existente, seleccione un objeto en la mesa de trabajo.  A continuación, en la parte superior de la mesa de trabajo, elija el botón de ruta de navegación, elija **Editar plantilla** y luego elija **Editar una copia** o **Crear vacío**.  
  
 Para crear un estilo, seleccione el objeto y, a continuación, en el menú **Objeto**, elija **Editar estilo** y después elija **Editar una copia** o **Crear vacío**.  
  
-   Elija **Editar una copia** para empezar con el estilo o la plantilla predeterminados del control.  
  
-   Elija **Crear vacío** para empezar desde cero.  
  
 La opción **Editar actual** solo aparece si edita un estilo o plantilla que ya ha creado,  pero no aparecerá para un control que sigue utilizando una plantilla predeterminada del sistema.  
  
 En el cuadro de diálogo **Crear recurso de estilo**, puede ponerle un nombre al estilo o a la plantilla para poder utilizarlo más adelante, o puede aplicar el estilo o la plantilla a todos los controles de ese tipo.  
  
> [!NOTE]
>  No es posible crear estilos o plantillas para todos los tipos control.  Si un control no los admite, el botón de ruta de navegación no aparecerá sobre la mesa de trabajo.  
>   
>  Para volver al ámbito de edición del documento principal, haga clic en **Devolver ámbito a**  ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3\-ed98\-4f20\-aa66\-a6f5b23eeb2b").  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Create a style](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Creating a Control Template in Expression Blend](http://msdn.microsoft.com/en-us/expression/cc263912.aspx).  
  
### Aplicar un estilo o una plantilla a un control  
 Haga clic con el botón derecho en el panel [Objetos y escala de tiempo](http://msdn.microsoft.com/es-es/135a5a5e-ec6d-4f38-8827-60e284cd5f57), elija **Editar plantilla** y después **Aplicar recurso**.  
  
### Restaurar el estilo o la plantilla predeterminados de un control  
 Seleccione el control y, en el panel [Propiedades](http://msdn.microsoft.com/es-es/135a5a5e-ec6d-4f38-8827-60e284cd5f57), busque la propiedad **Estilo** o **Plantilla**.  A continuación, haga clic en **Opciones avanzadas** ![](../designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962\-5d8a\-480d\-a837\-e06b84c545bb") y después haga clic en **￼Restablecer** en el menú contextual.  
  
##  <a name="Visual"></a> Estados visuales: cambiar la apariencia de un control según su estado  
 Los controles pueden tener una apariencia visual distinta según las interacciones del usuario.  Por ejemplo, cuando un usuario hace clic en un botón, puede hacer que este se vuelva verde o que se ejecute una animación.  El tiempo entre estados visuales se puede alargar o acortar mediante el uso de las transiciones.  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Manage the state of your WPF controls](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Recursos: crear colores, estilos y plantillas y volver a usarlos más adelante  
 Prácticamente cualquier elemento del proyecto se puede convertir en un recurso.  Un recurso es tan solo un objeto que se puede volver a usar en diferentes sitios de la aplicación.  Por ejemplo, puede crear un color, convertirlo en un recurso y después usar ese color en varios objetos.  Para cambiar el color de todos esos objetos, simplemente cambie el recurso de color.  
  
 **Vea un breve vídeo:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [A brief touch on resources](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## Vea también  
 [Creación de una interfaz de usuario con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)