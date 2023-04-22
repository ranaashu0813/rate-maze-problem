# rate-maze-problem
class Solution{
    public:
    bool issafe(int x, int y , vector<vector<int>>arr,vector<vector<bool>>&visited, int n ){
                
         
    if(visited[x][y]==false && (x>=0&&x<n) && (y>=0&&y<n) && arr[x][y]==1) {
        return true; 
    }        
    return false; 
                
    }
        void solve(int x1 , int y1 ,vector<vector<int>>arr, int n ,
vector<vector<bool>>&visited,vector<string>&ans, string path){
                
                
            if(x1==n-1 && y1==n-1){
                ans.push_back(path); 
                return 
            }
            visited[x1][y1] =1; 
            //four moment down , up , left and right
            
           if(issafe(x1+1, y1, arr , visited,n)){
               path+='D'; 
               solve(x1+1,y1,arr, n, visited, ans, path); 
           }
           
            if(issafe(x1-1, y1, arr , visited,n)){
               path+='U'; 
               solve(x1-1,y1,arr, n, visited, ans, path); 
           }
           
            if(issafe(x1, y1+1, arr , visited,n)){
               path+='R'; 
               solve(x1,y1+1,arr, n, visited, ans, path); 
           }
           
             if(issafe(x1+1, y1-1, arr , visited,n)){
               path+='L'; 
               solve(x1,y1-1,arr, n, visited, ans, path); 
           }
           visited[x1][y1] =1;
        }

    vector<string> findPath(vector<vector<int>> &m, int n) {
       vector<string>ans; 
     vector<vector<bool>>&visited(n,vector<bool>(n,0))
       string path = ""; 
       if(m[0][0]==0) return ans; 
       solve(0,0,m,n,visited,ans,path);
       
       return ans; 
    }
};
