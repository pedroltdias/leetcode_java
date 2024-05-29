# Resolução

```
class Solution {
    public int romanToInt(String s) {
        char[] symbolsToCharArray = s.toCharArray();
        int soma = 0;
        int valorAnterior = 0;

        for(char sym : symbolsToCharArray){
            RomanSymbolValue val = RomanSymbolValue.findEnumValueByString(sym);
            if (valorAnterior < val.getValue() && valorAnterior != 0){
                soma = soma + (val.getValue() - valorAnterior*2);
            } else {
                soma = soma + val.getValue();
            }
            valorAnterior = val.getValue();
        }


        return soma;
    }
}

enum RomanSymbolValue {

    SYMBOL_I('I', 1),
    SYMBOL_V('V', 5),
    SYMBOL_X('X', 10),
    SYMBOL_L('L', 50),
    SYMBOL_C('C', 100),
    SYMBOL_D('D', 500),
    SYMBOL_M('M', 1000);

    private char symbol;
    private int value;

    RomanSymbolValue(char symbol, int value){
        this.symbol = symbol;
        this.value = value;
    }

    public static RomanSymbolValue findEnumValueByString(char x){
        for(RomanSymbolValue rsv : values()){
            if(rsv.symbol == x){
                return rsv;
            }
        }
        return null;
    }

    public int getValue(){
        return this.value;
    }
}
```
