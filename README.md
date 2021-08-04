# LeetcodeSolution
The solutions for Leetcode 
第十四课
    字典树
	      顾名思义， 按照字典的方式(前缀)来存储单词，所以每个Node可以存map或int[26]
            class Trie {
                public Trie() { 
                    root = new Node(); 
                }
                public void insert(String word) { 
                    find(word, true, true); 
                }
                public boolean search(String word) { 
                    return find(word, true, false); 
                }
                public boolean startsWith(String prefix) { 
                    return find(prefix, false, false); 
                }
                
                class Node {
                    public int count;
                    public HashMap<Character, Node> child;
                    public Node() { 
                        count = 0; child = new HashMap<>(); 
                    }
                }
                Node root;
                boolean find(String s, boolean exact_match, boolean insert_if_not_exist) {
                    Node curr = root;
                    for (Character c : s.toCharArray()) {
                        if (!curr.child.containsKey(c)) {
                            if (!insert_if_not_exist) 
                                return false;
                            curr.child.put(c, new Node());
                        }
                        curr = curr.child.get(c);
                    }
                    if (insert_if_not_exist) 
                        curr.count++;
                    return exact_match ? curr.count > 0 : true;
                }
            }
            
并查集
    不相交集合：只关注自己的父亲是谁，有一样的father就来自同一交集
        class DisjointSet {
            int[] fa;
            public DisjointSet(int n) {
                fa = new int[n];
                for (int i = 0; i < n; i++)
                    fa[i] = i;
            }
	
            public int find(int x) {
                if (x == fa[x])
                    return x;	
                return fa[x] = find(fa[x]);
                // return x == fa[x] ? x : (fa[x] = find(fa[x]));
            }

            public void union(int x, int y) {
                x = find(x);
                y = find(y);
                if (x != y)
                    fa[x] = y;
            }
        }
