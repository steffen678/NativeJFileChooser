# NativeJFileChooser

This is a drop-in replacement for Swing's file chooser. Instead of displaying
the Swing file chooser, it makes use of the JavaFX file chooser if available.
It still uses Swing's file chooser as a fallback. 

## Usage

NativeJFileChooser is available via Maven:

    <dependency>
        <groupId>li.flor</groupId>
        <artifactId>native-j-file-chooser</artifactId>
        <version>1.6.4</version>
    </dependency>

Simply replace

    JFileChooser fileChooser = new JFileChooser();

with

    JFileChooser fileChooser = new NativeJFileChooser();

## Example

    EventQueue.invokeLater(() -> {
        JFrame frame = new JFrame("Test");
        JButton button = new JButton("Click me!");
        JFileChooser fileChooser = new NativeJFileChooser();
        fileChooser.setFileFilter(new FileNameExtensionFilter("JPG", "*.jpg"));
        button.addActionListener((ActionEvent e) -> {
            fileChooser.showDialog(frame, "Open");
        });
        frame.add(button);
        frame.setLocationRelativeTo(null);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.pack();
        frame.setVisible(true);
    });
