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
        // 构建词频向量
        // 计算余弦相似度
