---
title: 'Cómo: agregar validación a clases de entidad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665994"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procedimiento para agregar validación a clases de entidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Validar* las clases de entidad es el proceso de confirmar que los valores especificados en los objetos de datos cumplen las restricciones en el esquema de un objeto, además de las reglas establecidas para la aplicación. Se recomienda validar los datos antes de enviar las actualizaciones a la base de datos subyacente para reducir los errores. De este modo, también se reduce el número de viajes de ida y vuelta entre una aplicación y la base de datos.

 Las [herramientas de LINQ to SQL de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) proporcionan métodos parciales que permiten a los usuarios extender el código generado por el diseñador que se ejecuta durante las inserciones, actualizaciones y eliminaciones de entidades completas, y también durante y después de los cambios de columna individuales.

> [!NOTE]
> En este tema se proporcionan los pasos básicos para agregar validación a las clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Dado que podría resultar difícil seguir estos pasos genéricos sin hacer referencia a una clase de entidad concreta, se ha proporcionado un tutorial con datos reales.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Agregar validación para los cambios realizados en el valor de una columna concreta
 En este procedimiento se muestra cómo validar datos cuando cambia el valor en una columna. Dado que la validación se realiza en la definición de clase (en lugar de la interfaz de usuario), se genera una excepción si el valor no puede validarse. Implemente un control de errores para el código en la aplicación que intenta cambiar los valores de columna.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Para validar los datos mientras se modifican los valores de una columna

1. Abra o cree un nuevo archivo de clases de LINQ to SQL (archivo **. dbml** ) en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Haga doble clic en el archivo **.dbml** en el **Explorador de soluciones**).

2. En Object Relational Designer, haga clic con el botón secundario en la clase para la que desea agregar la validación y, a continuación, haga clic en **Ver código**.

    El Editor de código se abre con una clase parcial para la clase de entidad seleccionada.

3. Coloque el cursor en la clase parcial.

4. Para proyectos de Visual Basic:

   1. Expanda la lista **Nombre de método**.

   2. Busque el método de**cambio** **en**_COLUMNNAME_para la columna a la que desea agregar la validación.

   3. `On` *COLUMNNAME* `Changing` Se agrega un método COLUMNNAME a la clase parcial.

   4. Agregue el código siguiente para comprobar, en primer lugar, que se ha especificado un valor y, a continuación, para asegurar que el valor especificado para la columna es aceptable para la aplicación. El argumento `value` contiene el valor propuesto, por lo que debe agregar la lógica para confirmar que es un valor válido:

      ```vb
      If value.HasValue Then
          ' Add code to ensure that the value is acceptable.
          ' If value < 1 Then
          '    Throw New Exception("Invalid data!")
          ' End If
      End If
      ```

      Para proyectos de C#:

   5. Dado que los proyectos de C# no generan automáticamente los controladores de eventos, puede usar IntelliSense para crear los métodos parciales de cambio de columna.

       Escriba `partial` y, a continuación, un espacio para obtener acceso a la lista de métodos parciales disponibles. Haga clic en el método de cambio de columna correspondiente a la columna a la que desee agregar validación. El código siguiente es similar al código que se genera al seleccionar un método parcial de cambio de columna:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Agregar validación para las actualizaciones de una clase de entidad
 Además de comprobar los valores durante los cambios, también puede validar los datos cuando se intenta actualizar una clase de entidad completa. La validación durante un intento de actualización permite comparar los valores de varias columnas si lo requieren las reglas del negocio. En el procedimiento siguiente se muestra cómo validar cuando se intenta actualizar una clase de entidad completa.

> [!NOTE]
> El código de validación para las actualizaciones de clases de entidad completas se ejecuta en la clase <xref:System.Data.Linq.DataContext> parcial (en lugar de la clase parcial de una clase de entidad concreta).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Para validar datos durante la actualización de una clase de entidad

1. Abra o cree un nuevo archivo de clases de LINQ to SQL (archivo **. dbml** ) en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Haga doble clic en el archivo **.dbml** en el **Explorador de soluciones**).

2. Haga clic con el botón derecho del mouse en un área vacía de Object Relational Designer y, a continuación, haga clic en **Ver código**.

    El Editor de código se abre con una clase parcial para `DataContext`.

3. Coloque el cursor en la clase parcial para `DataContext`.

4. Para proyectos de Visual Basic:

   1. Expanda la lista **Nombre de método**.

   2. Haga clic en **Actualizar**_nombredeclasedeentidad_.

   3. Un `Update` método *nombredeclasedeentidad* se agrega a la clase parcial.

   4. Obtenga acceso a los valores de la columna mediante el argumento `instance`, como se muestra en el código siguiente:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Para proyectos de C#:

   5. Dado que los proyectos de C# no generan automáticamente los controladores de eventos, puede usar IntelliSense para crear el `Update` método parcial *className* .

   6. Escriba `partial` y, a continuación, un espacio para obtener acceso a la lista de métodos parciales disponibles. Haga clic en el método de actualización de la clase a la que desee agregar validación. El código siguiente es similar al código que se genera al seleccionar un `Update` método parcial *className* :

      ```csharp
      partial void UpdateCLASSNAME(CLASSNAME instance)
      {
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
          {
              string ErrorMessage = "Invalid data!";
              throw new System.Exception(ErrorMessage);
          }
      }
      ```

## <a name="see-also"></a>Consulte también
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [validar datos](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
