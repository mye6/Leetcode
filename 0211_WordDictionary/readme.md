
## Solution 1 (CPP). Trie
```cpp
// Time: add word O(W), search O(W); W is the lenght of the word
// Space: O(W)
class WordDictionary {
public:
    
    struct TrieNode {
        bool isWord;
        vector<TrieNode*> child;
        TrieNode() : isWord(false), child(26,nullptr) { }
    };
    
    TrieNode* root;
    
    WordDictionary() : root(new TrieNode) { }
    
    void addWord(string word) {
        auto p=root;
        for(char c : word) {
            if(!p->child[c-'a'])
                p->child[c-'a']=new TrieNode();
            
            p=p->child[c-'a'];
        }
        p->isWord=true;
    }
    bool match(string& word, int pos, TrieNode* p) {
        if(pos==word.size()) return p->isWord;
        
        char c=word[pos];
        if(c!='.')
            return p->child[c-'a'] && match(word,pos+1,p->child[c-'a']);
        
        for(auto nxt : p->child) {
            if(nxt && match(word,pos+1,nxt)) return true;
        }
        return false;
    }
    
    bool search(string word) {
        return match(word,0,root);    
    }
    
    
};

```
