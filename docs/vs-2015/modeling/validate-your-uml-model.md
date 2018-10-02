---
title: Validar el modelo UML | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 42e0733668a1f96dc1881d4d4d58a575eeb9eb64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574673"
---
# <a name="validate-your-uml-model"></a>Validar el modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [validar el modelo UML](https://docs.microsoft.com/visualstudio/modeling/validate-your-uml-model).  
  
Algunos de los modelos UML que trace en Visual Studio podrían no ser válidos en el proyecto. Por ejemplo, quizá desee que un caso de uso esté siempre vinculado a un diagrama de secuencia, y que este diagrama tenga líneas de vida que representen los actores del caso de uso. Puede instalar o definir *restricciones* que ayudan a su equipo satisfaga requisitos como este. Las restricciones se pueden aplicar cuando el usuario guarda o abre un modelo y se pueden invocar mediante un comando de menú.  
  
 Con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] no se proporcionan restricciones, ya que dependen de cómo el equipo interpreta y usa los modelos UML. Sin embargo, puede definir sus propias restricciones e instalar restricciones definidas por otros usuarios. Para obtener información sobre cómo definir restricciones y empaquetarlas para su distribución, consulte [definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
## <a name="invoking-validation"></a>Invocar la validación  
 Cuando se ha instalado una extensión de validación, las restricciones que proporciona se pueden aplicar en los casos siguientes. Algunas restricciones están configuradas para aplicarse únicamente en algunos de estos casos.  
  
-   **Comando de validación.** Para invocar la validación en cualquier momento, haga clic en **validar modelo UML** en el **arquitectura** menú.  
  
    > [!NOTE]
    >  El comando solo aparecerá si se instalan las restricciones de validación.  
  
-   **Al guardar un modelo.** Las restricciones de validación se pueden aplicar al guardar el modelo. El propósito de estas restricciones es asegurarse de que no se guarda un modelo que no es válido según la interpretación del proyecto.  
  
     Si hay errores, se le pedirá si quiere guardar el modelo. Puede corregir los errores o guardar el modelo de todos modos.  
  
-   **Al abrir un modelo.** Cuando se abre un modelo, pueden aplicarse métodos de validación para restaurar los mensajes de error que existían cuando se guardó el modelo. Es posible que se produzcan errores por incoherencias entre los cambios realizados por los usuarios que trabajan en diferentes partes de un modelo. Para obtener más información, consulte [compartir modelos y exportar diagramas](../modeling/share-models-and-exporting-diagrams.md).  
  
 Los errores de validación se notifican en la ventana de errores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Para seleccionar en un diagrama los elementos que no son correctos, haga doble clic en el error. Esto solo funciona si los elementos incorrectos son visibles en un diagrama abierto.  
  
## <a name="installing-validation-constraints"></a>Instalar restricciones de validación  
 Las restricciones van empaquetadas dentro de archivos de extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Normalmente, un conjunto de restricciones formará parte de una extensión que también contenga otras definiciones, como comandos de menú, perfiles y elementos de cuadro de herramientas.  
  
#### <a name="to-install-a-visual-studio-extension"></a>Para instalar una extensión de Visual Studio  
  
1.  Haga doble clic en el **.vsix** archivo en el Explorador de Windows (o explorador de archivos).  
  
2.  Reinicie cualquier instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que ya se esté ejecutando.  
  
## <a name="disabling-and-uninstalling-validation-constraints"></a>Deshabilitar y desinstalar restricciones de validación  
 Si desea trabajar con un modelo en el que no se aplican las restricciones, puede deshabilitar temporalmente la extensión que los contiene. De esta manera, habilitando y deshabilitando las extensiones, puede trabajar con distintos tipos de modelo en momentos diferentes.  
  
#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Para deshabilitar o desinstalar una extensión de Visual Studio  
  
1.  En el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **herramientas** menú, haga clic en **extensiones y actualizaciones**.  
  
2.  Junto con la extensión, haga clic en **deshabilitar** para deshabilitar temporalmente la extensión. Se puede volver a habilitarla más adelante mediante la devolución a la **extensiones y actualizaciones** ventana.  
  
     \- o -  
  
     Haga clic en **desinstalar** para quitar la extensión.  
  
3.  Reinicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Definir restricciones de validación para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)   
 [Usar modelos en el proceso de desarrollo](../modeling/use-models-in-your-development-process.md)



