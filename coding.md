
######shortcuts,

-[shortcut](https://www.shortcutfoo.com/)

#### coding,
Below is the coding

    List<Integer> someItems = Arrays.asList(new Integer[] {1, 2, 3, 4});
    for (Integer item : someItems) {
           System.out.println(item);
    }
    Map<String, String> someMapping = new HashMap<String , String>() {{
          put("ST", "started);
          put("IP", "in progress");
          put("DN", "done");
    }}
    for (Map.Entry<String, String> entry : someMapping.entrySet()) {
            String key = entry.getKey();
            String value = entry.getValue();
            System.out.println(key + " => " + value);
    }
