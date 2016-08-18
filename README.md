# machineIntelli
machine learning

My name is Thomas. I have a dream to build a really intelligent robot that will serve me like a king! lol :).

class Solution {
private:
    vector<int> max;
    vector<int> min;
    
public:
    void Insert(int num)
    {
        if(max.size() <= min.size())
            {
            max.push_back(num);
        	percolateUp0(max, num);
        } 
        else
            {
            min.push_back(num);
        	percolateUp1(min, num);
        }
        if(!max.empty() && !min.empty() && max[0] > min[0])
        {
            int top = max[0];
            max[0] = min[0];
            min[0] = top;
        }
    }

    double GetMedian()
    { 
    	if (max.size()>min.size()) return max[0];
        else return ((max[0]+min[0])/2);
    }
    
    void percolateUp0(vector<int> &vec, int num)
        {
        int i = vec.size()-1;
        while (vec[(i-1)/2])
            {
            int j = (i-1)/2;
            if (num < vec[j]) 
                return;
            else
            {
            vec[i] = vec[j];
            vec[j] = num;
            i = j;
        	}
        }     
    }
    
   void percolateUp1(vector<int> &vec)
        {
        int c = vec.size()-1;
        int p = (c-1)/2;
        int tmp = vec[c];
        while (c>0)
            {
            if (vec[p] < tmp) 
                return;
            else
            {
            vec[c] = vec[p];
            c = p;
            p = (p-1)/2;
        	}
        }
        vec[c] = tmp;
    }

};
