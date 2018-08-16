---
title: 'Cómo: Cambiar el espacio de nombres de los lenguajes específicos de dominio'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1963502f3940fd0d17c770f111e07de14207e687
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948267"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Cómo: Cambiar el espacio de nombres de los lenguajes específicos de dominio
Puede cambiar el espacio de nombres de un lenguaje específico de dominio. Debe realizar el cambio en el **DSL explorador**, en las propiedades del proyecto de paquete de Dsl y en la información de ensamblado.

### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para cambiar el espacio de nombres de un lenguaje específico de dominio

1.  En **DSL explorador**, haga clic en el **Dsl** nodo.

2.  En el **propiedades** ventana, cambiar la **Namespace** propiedad.

3.  Guarde la solución y transformar las plantillas.

4.  En el **proyecto** menú, haga clic en **Dsl propiedades**.

     Aparecerán las propiedades del proyecto.

5.  Haga clic en la pestaña **Aplicación** .

6.  Cambiar el **espacio de nombres predeterminado** propiedad para el nuevo nombre de espacio de nombres.

7.  Si también desea cambiar el nombre del ensamblado, cambie la **propiedad de nombre de ensamblado.**

8.  Si ha cambiado el nombre del ensamblado, abra DslPackage\Package.tt y actualice esta línea:

     `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si ha escrito un código personalizado, asegúrese de cambiar las referencias de espacio de nombres y la clase en los archivos de código.

10. Restablecer la instancia Experimental de Visual Studio.

    1.  Eliminar **\Users\\ ***{su nombre}*** \AppData\Local\Microsoft\VisualStudio\\\*Exp**

    2.  En las ventanas **iniciar** menú, elija **todos los programas**, **Microsoft Visual Studio 2010 SDK**, **herramientas**, **restablecer el Instancia experimental**.

11. En el **generar** menú, elija **volver a generar solución**.

## <a name="see-also"></a>Vea también

- [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)