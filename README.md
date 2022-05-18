# Java Introducción 

* ## **Palabra Static**

Cuando un **miembro** se declara **static**, se puede acceder antes de crear cualquier objeto de su clase y sin referencian de ningún objeto. 

Por ejemplo tenemos la clase **Temporizador** y tiene una variable **static int contar**, la asignación seria de la siguiente manera: 
```
Temporizador.contar = 10; 
```
Se utiliza la clase y posteriormente se accede a la variable static. Funcionado de la misma forma si se tiene un método estático.

`static` es un modificador de no acceso en Java que se aplica en: 
* Variables.
* Metodos.
* Bloques.
* Clases anidadas. 

### **Variables**
Las variables `static` son variables globales. Cuando se declara en un objeto no se realiza una copia de una variable estática. En cambio todas las instancias de la clase comparten la misma variable estática. Por ejemplo: 
```
class StaticDemo
{
    int x; //Variable de instancia normal
    static int y; //Variable estática
    //Retornar la suma de la variable de instancia 'x'
    //y la variable estática 'y'
    int suma(){
        return x+y;
    }
}
class Test{
    public static void main(String[] args) {
        StaticDemo ob1=new StaticDemo();
        StaticDemo ob2=new StaticDemo();
        //Cada objeto tiene su propia copia de una variable de instancia
        ob1.x=10;
        ob2.x=12;
        System.out.println("Por supuesto, ob1.x y ob2.x son independientes.");
        System.out.println("ob1.x: "+ob1.x+"\nob2.x: "+ob2.x);
        System.out.println();
        //Cada objeto comparte una copia de una variable estática
        System.out.println("La variable estática 'y' es compartida.");
        StaticDemo.y=100;
        System.out.println("Cambio de StaticDemo.y a 100");
        System.out.println("ob1.suma(): "+ob1.suma());
        System.out.println("ob2.suma(): "+ob2.suma());
    }
}
```
La variable `y` es compartida por `ob1` y `ob2`. Cambiarlo afecta a toda la clase y no solo a una instancia. 

### **Metodos**
Un metodo estático ***se llama a través de su nombre de clase, sin que se cree ningun objeto de esa clase***. Entonces: 

```
// Ejemplo de método estático
class StaticDemo
{
   static int valor=1024; //Una variable estática
   //Un método estático
   static int valDiv2(){
       return valor/2;
   }
}
class Test{
    public static void main(String[] args) {
        System.out.println("El valor es: "+StaticDemo.valor);
        System.out.println("StaticDemo.valDiv2(): "+StaticDemo.valDiv2());
        StaticDemo.valor=4;
        System.out.println("El valor es: "+StaticDemo.valor);
        System.out.println("StaticDemo.valDiv2(): "+StaticDemo.valDiv2());
    }
}
```
Los **metodos estáticos tienen varias retricciones:**
1. Pueden llamar directamente solo a los otros metodos estaticos de su clase. 
2. Pueden acceder directamente solo a variables estaticas de su clase. 
3. Ellos no tiene una referencia `this`. 