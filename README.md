# fabrica-de-silla-method


import java.util.Scanner;

// Interfaz para los productos (sillas y mesas)
interface Furniture {
    void create();
}

// Clase concreta para sillas
class Chair implements Furniture {
    private String style;
    private String color;
    private String material;

    public Chair(String style, String color, String material) {
        this.style = style;
        this.color = color;
        this.material = material;
    }

    @Override
    public void create() {
        System.out.println("Se ha creado una silla " + style + " de color " + color + " hecha de " + material + ".");
    }
}

// Clase concreta para mesas
class Table implements Furniture {
    private String style;
    private String color;
    private String material;

    public Table(String style, String color, String material) {
        this.style = style;
        this.color = color;
        this.material = material;
    }

    @Override
    public void create() {
        System.out.println("Se ha creado una mesa " + style + " de color " + color + " hecha de " + material + ".");
    }
}

// Fábrica abstracta para crear productos Furniture
abstract class FurnitureFactory {
    // El método factoryMethod que debe ser implementado por las subclases
    public abstract Furniture createFurniture(String style, String color, String material);
}

// Fábrica concreta para sillas
class ChairFactory extends FurnitureFactory {
    @Override
    public Furniture createFurniture(String style, String color, String material) {
        return new Chair(style, color, material);
    }
}

// Fábrica concreta para mesas
class TableFactory extends FurnitureFactory {
    @Override
    public Furniture createFurniture(String style, String color, String material) {
        return new Table(style, color, material);
    }
}

public class fabrica {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Crear una silla:");
        System.out.print("Estilo: ");
        String chairStyle = scanner.nextLine();
        System.out.print("Color: ");
        String chairColor = scanner.nextLine();
        System.out.print("Material: ");
        String chairMaterial = scanner.nextLine();

        FurnitureFactory chairFactory = new ChairFactory();
        Furniture chair = chairFactory.createFurniture(chairStyle, chairColor, chairMaterial);
        chair.create();

        System.out.println("\nCrear una mesa:");
        System.out.print("Estilo: ");
        String tableStyle = scanner.nextLine();
        System.out.print("Color: ");
        String tableColor = scanner.nextLine();
        System.out.print("Material: ");
        String tableMaterial = scanner.nextLine();

        FurnitureFactory tableFactory = new TableFactory();
        Furniture table = tableFactory.createFurniture(tableStyle, tableColor, tableMaterial);
        table.create();
    }
}
