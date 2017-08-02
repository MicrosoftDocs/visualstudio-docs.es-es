---
title: Modificar el estilo de objetos en Blend | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31192d2c-5b84-41bc-94c0-898638c170bd
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 77138e9a2c724b4a42e289556f7d1fa294aac0f0
ms.contentlocale: es-es
ms.lasthandoff: 05/13/2017

---
# <a name="modify-the-style-of-objects-in-blend"></a>Modificar el estilo de objetos en Blend
La manera más fácil de personalizar un objeto es establecer propiedades en el panel **Propiedades**.  
  
 Si desea volver a utilizar la configuración o un conjunto de configuraciones, cree un recurso reutilizable. Podría tratarse de un *estilo*, una *plantilla* o algo simple como un color personalizado. También puede hacer la apariencia de un control sea distinta en función de su estado. Por ejemplo, que un botón se vuelva verde cuando el usuario haga clic en él.  
  
 **En este tema**:  
  
-   [Pinceles: modificar la apariencia de un objeto](#Brushes)  
  
-   [Estilos y plantillas: crear una apariencia coherente en todos los controles](#Styles)  
  
-   [Estados visuales: Cambiar la apariencia de un control según su estado](#Visual)  
  
-   [Recursos: crear colores, estilos y plantillas y volver a usarlos más adelante](#Resources)  
  
##  <a name="Brushes"></a>Pinceles: modificar la apariencia de un objeto  
 Aplique un pincel a un objeto si desea cambiar su apariencia.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Editor de pinceles](http://www.popscreen.com/v/6A4mO/Microsoft-Expression-Blend-The-Brushes-Editor).  
  
### <a name="paint-a-repeating-image-or-pattern-on-an-object"></a>Pintar una imagen o patrón repetitivos en un objeto  
 Pinte una imagen o patrón repetitivos en un objeto con un *pincel de diseño en mosaico*.  
  
 Para crear un pincel de diseño en mosaico, empiece por crear un recurso de *pincel de imagen*, *pincel con dibujo* o *pincel visual*.  
  
 Cree un pincel de imagen con una imagen. Las ilustraciones siguientes muestran el pincel de imagen, el pincel de imagen en mosaico y el pincel de imagen volteado.  
  
 ![](~/designers/media/81f84f56-906d-456b-8288-d77da1e01e31.png "81f84f56-906d-456b-8288-d77da1e01e31") ![](~/designers/media/d3782ca8-64da-47a4-a095-c6cdd0fa47a2.png "d3782ca8-64da-47a4-a095-c6cdd0fa47a2") ![](~/designers/media/38ae3691-f3f1-4a1e-82ca-c7fa164bf56e.png "38ae3691-f3f1-4a1e-82ca-c7fa164bf56e")  
  
 Cree un pincel con dibujo mediante un dibujo vectorial como un trazado o forma. Las ilustraciones siguientes muestran el pincel con dibujo, el pincel con dibujo en mosaico y el pincel con dibujo volteado.  
  
 ![](~/designers/media/197666ac-ef57-4c5c-9779-669e991a00a5.png "197666ac-ef57-4c5c-9779-669e991a00a5") ![](~/designers/media/ba09cda3-4cee-40ba-b3d4-edc032158bdc.png "ba09cda3-4cee-40ba-b3d4-edc032158bdc") ![](~/designers/media/15bf6021-620c-4490-9eae-086153d3f14f.png "15bf6021-620c-4490-9eae-086153d3f14f")  
  
 Cree un pincel visual a partir de un control como un botón. Las ilustraciones siguientes muestran el pincel visual y el pincel visual en mosaico.  
  
 ![](~/designers/media/fb6c90e0-153c-48fe-b563-e601beac6227.png "fb6c90e0-153c-48fe-b563-e601beac6227") ![](~/designers/media/e261b99f-7d8f-4d91-bc84-19c7beccc255.png "e261b99f-7d8f-4d91-bc84-19c7beccc255")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Pinceles de diseño en mosaico](http://www.popscreen.com/v/6A4iM/Microsoft-Expression-Blend-Tile-Brushes).  
  
##  <a name="Styles"></a> Estilos y plantillas: crear una apariencia coherente en todos los controles  
 Puede diseñar la apariencia y el comportamiento de un control una vez y aplicar ese diseño a otros controles para no tener que hacerlo de manera individual.  
  
 **¿Debe usar un estilo?**: Si quiere establecer las propiedades predeterminadas (como el color de un botón), use un *estilo*. Puede modificar un control incluso después de aplicarle un estilo.  
  
 **¿Debe usar una plantilla?**: Si quiere cambiar la estructura de un control, use una *plantilla*. Imagine que convierte un gráfico o un logotipo en un botón. El control no se puede modificar después de aplicarle una plantilla.  
  
### <a name="create-a-template-or-style"></a>Crear una plantilla o un estilo  
 Hay dos maneras de crear una plantilla. puede convertir cualquier objeto de la mesa de trabajo en un control o puede basar la plantilla en un control existente.  
  
 Para convertir cualquier objeto en una plantilla de control, seleccione el objeto y, después, en el menú **Herramientas**, pulse **Crear en control**.  
  
 Si desea basar la plantilla en un control existente, seleccione un objeto en la mesa de trabajo. Después, en la parte superior de la mesa de trabajo, pulse el botón de ruta de navegación, pulse **Editar plantilla** y, después, seleccione **Editar una copia** o **Crear vacío**.  
  
 ![](~/designers/media/5ebdb33f-aad2-4c10-a328-5e8b04c56a36.png "5ebdb33f-aad2-4c10-a328-5e8b04c56a36")  
  
 Para crear un estilo, seleccione el objeto y, después, en el menú **Objeto**, pulse **Editar estilo** y, después, pulse **Editar una copia** o **Crear vacío**.  
  
-   Seleccione **Editar una copia** para empezar con el estilo o la plantilla predeterminados del control.  
  
-   Seleccione **Crear vacío** para empezar desde cero.  
  
 La opción **Editar actual** solo aparece si edita un estilo o plantilla que ya ha creado, pero no aparecerá para un control que sigue usando una plantilla predeterminada del sistema.  
  
 En el cuadro de diálogo **Crear recurso de estilo**, puede ponerle un nombre al estilo o a la plantilla para poder usarlo más adelante, o puede aplicar el estilo o la plantilla a todos los controles de ese tipo.  
  
 ![](~/designers/media/4818ee6a-ce60-4b79-91c8-3b1871829eea.png "4818ee6a-ce60-4b79-91c8-3b1871829eea")  
  
> [!NOTE]
>  No es posible crear estilos o plantillas para todos los tipos control. Si un control no los admite, el botón de ruta de navegación no aparecerá sobre la mesa de trabajo.  
>   
>  Para volver al ámbito de edición del documento principal, haga clic en **Devolver ámbito a**  ![](../designers/media/55844eb3-ed98-4f20-aa66-a6f5b23eeb2b.png "55844eb3-ed98-4f20-aa66-a6f5b23eeb2b").  
>   
>  ![](~/designers/media/4a5612e1-7a28-4587-b870-0fe7112ec2ad.png "4a5612e1-7a28-4587-b870-0fe7112ec2ad")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear un estilo](http://www.microsoft.com/showcase/details.aspx?uuid=9b8e86e2-8e90-4d61-81af-fa5b5afb3e95).  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear una plantilla de control en Expression Blend](http://msdn.microsoft.com/expression/cc263912.aspx).  
  
### <a name="apply-a-style-or-template-to-a-control"></a>Aplicar un estilo o una plantilla a un control  
 Haga clic con el botón derecho en el panel [Objetos y escala de tiempo](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57), pulse **Editar plantilla** y, después, **Aplicar recurso**.  
  
 ![](~/designers/media/dc12debc-7711-47d9-84ce-10322a384397.png "dc12debc-7711-47d9-84ce-10322a384397")  
  
### <a name="restore-the-default-style-or-template-of-a-control"></a>Restaurar el estilo o la plantilla predeterminados de un control  
 Seleccione el control y, en el panel [Propiedades](http://msdn.microsoft.com/en-us/135a5a5e-ec6d-4f38-8827-60e284cd5f57), busque la propiedad **Estilo** o **Plantilla**. Después, haga clic en **Opciones avanzadas** ![](~/designers/media/12e06962-5d8a-480d-a837-e06b84c545bb.png "12e06962-5d8a-480d-a837-e06b84c545bb") y, después, haga clic en **Restablecer** en el menú contextual.  
  
##  <a name="Visual"></a> Estados visuales: Cambiar la apariencia de un control según su estado  
 Los controles pueden tener una apariencia visual distinta según las interacciones del usuario. Por ejemplo, cuando un usuario hace clic en un botón, puede hacer que este se vuelva verde o que se ejecute una animación. El tiempo entre estados visuales se puede alargar o acortar mediante el uso de las transiciones.  
  
 ![](~/designers/media/a95c671a-5639-40b9-83db-1e6b214330d5.png "a95c671a-5639-40b9-83db-1e6b214330d5")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Administrar el estado de los controles de WPF](https://www.youtube.com/watch?v=m0PlkF5i6uw).  
  
##  <a name="Resources"></a> Recursos: crear colores, estilos y plantillas y volver a usarlos más adelante  
 Prácticamente cualquier elemento del proyecto se puede convertir en un recurso. Un recurso es tan solo un objeto que se puede volver a usar en diferentes sitios de la aplicación. Por ejemplo, puede crear un color, convertirlo en un recurso y después usar ese color en varios objetos. Para cambiar el color de todos esos objetos, simplemente cambie el recurso de color.  
  
 ![](~/designers/media/89203705-cf66-46e0-b153-52a23cd744f7.png "89203705-cf66-46e0-b153-52a23cd744f7") ![](~/designers/media/6bff8b19-3cd5-41a0-bbf9-ff65532d5aae.png "6bff8b19-3cd5-41a0-bbf9-ff65532d5aae")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](~/designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Breve información sobre los recursos](http://www.popscreen.com/v/6A4k7/Microsoft-Expression-Blend-Brief-Touch-on-Resources).  
  
## <a name="see-also"></a>Vea también  
 [Crear una IU con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
