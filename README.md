 public class PaperCheck {
     public static void main(String[] args) throws IOException {
            // 从命令行参数读取文件路径
            // 读取文件内容并分词
            // 计算词频
            // 构建词汇表
            // 构建词向量
            // 计算余弦相似度
            // 将结果输出到文件中，保留两位小数
     }

        // 读取文件并分词
        private static List<String> tokenizeFile(String filePath) throws IOException {
        String content = Files.readString(Paths.get(filePath));
        return Arrays.stream(content.split("\\W+"))  // 分词，使用正则表达式去掉标点符号
                     .filter(word -> !word.isEmpty())
                     .collect(Collectors.toList());
    }
        // 构建词频表
        private static Map<String, Integer> buildWordFrequency(List<String> words) {
        Map<String, Integer> wordFreq = new HashMap<>();
        for (String word : words) {
            wordFreq.put(word, wordFreq.getOrDefault(word, 0) + 1);
        }
        return wordFreq;
    }

        // 构建词频向量
           private static List<Integer> buildVector(Set<String> allWords, Map<String, Integer> wordFreq) {
        List<Integer> vector = new ArrayList<>();
        for (String word : allWords) {
            vector.add(wordFreq.getOrDefault(word, 0));
        }
        return vector;
    }
        // 计算余弦相似度
        private static double calculateCosineSimilarity(List<Integer> vectorA, List<Integer> vectorB) {
        int dotProduct = 0;
        int normA = 0;
        int normB = 0;
        for (int i = 0; i < vectorA.size(); i++) {
            dotProduct += vectorA.get(i) * vectorB.get(i);
            normA += vectorA.get(i) * vectorA.get(i);
            normB += vectorB.get(i) * vectorB.get(i);
        }
        return dotProduct / (Math.sqrt(normA) * Math.sqrt(normB));
    }


