import java.util.ArrayList;
import java.util.List;
public class SalesAnalysis {
    private static final String[] PRODUCTS = {"Tea", "Coffee", "GreenTea", "LemonTea", "Soda", "Limca"};
    private static final double[] SALES_2021 = {100.0, 129.0, 140.0, 167.0, 267.0, 873.0};
    private static final double[] SALES_2022 = {120.0, 234.0, 168.0, 345.0, 987.0, 983.0};

    public static void main(String[] args) {
        List<Product> products = new ArrayList<>();
        for (int i = 0; i < PRODUCTS.length; i++) {
            products.add(new Product(PRODUCTS[i], SALES_2021[i], SALES_2022[i]));
        }

        System.out.println("Product\t\tSales2021\tSales2022\tVariance\tVariancePct\tTotal");
        for (Product p : products) {
            System.out.printf("%s\t\t%.2f\t\t%.2f\t\t%.2f\t\t%.2f%%\t\t%.2f\n",
                    p.name, p.sales2021, p.sales2022, p.variance(), p.variancePct(), p.total());
        }
    }

    static class Product {
        private final String name;
        private final double sales2021;
        private final double sales2022;

        Product(String name, double sales2021, double sales2022) {
            this.name = name;
            this.sales2021 = sales2021;
            this.sales2022 = sales2022;
        }

        double variance() {
            return sales2022 - sales2021;
        }

        double variancePct() {
            return (sales2022 - sales2021) / sales2021 * 100;
        }

        double total() {
            return sales2021 + sales2022;
        }
    }
}
