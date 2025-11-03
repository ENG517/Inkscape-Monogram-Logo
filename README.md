# DITA Demo - Creating a Monogram Logo in Inkscape

## Conditional Outputs: novice vs. expert

1. Decide what content can be flagged as needed for “novice” and “expert” audiences respectively.
2. Scope content in your model with audience attribute with either values of novice or expert:
    ```xml
    <step audience="novice">
      ...
    </step>
    ```

    or

    ```xml
    <section audience="expert">
      <title>Expert Only Content!</title>
      ...
    </section>
    ```
3. Create a .ditaval file, such as this example that can filter out expert-level content:
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <val>
      <prop att="audience"
            val="novice"
            action="include"
      />
      <prop att="audience"
            val="expert"
            action="exclude"
      />
    </val>
    ```

4. Run the dita command with the --filter parameter that points to the ditaeval file.
    ```bash
    dita -i _sequence.ditamap -f pdf --filter novice.ditaval -o out/pdf/novice
    ```

    or

    ```bash
    dita -i _sequence.ditamap -f pdf --filter expert.ditaval -o out/pdf/expert
    ```