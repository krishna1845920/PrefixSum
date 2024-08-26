# PrefixSum
import java.util.Scanner;

public class prefsumm {
    static void findPrefixSumMatrix(int [][] matix){
        int r=matix.length; 
        int c=matix[0].length;
        //traverse horizontally to calculate row wise prefix sum]
        for (int i=0 ; i<r; i++){
            for(int j=1; j<c; j++){
                matix[i][j]+=matix[i][j-1];

            }
        }
        //traverse vertically to calculate column wise prefix sum]
         for(int j=0; j<c; j++){
            for(int i=1; i<r; i++){
                matix[i][j]+=matix[i-1][j];
            }
         }


    }
    static int findsum3(int[][] matrix,int l1,int r1,int l2,int r2){ 
        findPrefixSumMatrix(matrix);
        int ans=0, sum=0, up=0, left =0, leftup=0;
        sum=matrix[l2][r2];
        if(r1>0)
        left = matrix [l2][r1-1];
        if(r1>0)
        up=matrix[l1-1][r2];
        if(r1>0 && r1>0)
        leftup=matrix[l1-1][r1-1];
        ans=sum-up-left+leftup;
        return ans;  
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner (System.in);
        System.out.println("Enter no of rows and column of matrix : ");
        int r=sc.nextInt(); 
        int c=sc.nextInt(); 
        int matix[][]=new int [r][c];
        System.out.println("Enter Elements of matrix : ");
        for(int i=0; i<r; i++){
            for(int j=0; j<c; j++){
                matix[i][j]=sc.nextInt(); 
            }
        }
        System.out.println("Enter rectangle boundries l1 , r1, l2, r2 ");
        int l1=sc.nextInt(); 
        int r1=sc.nextInt(); 
        int l2=sc.nextInt(); 
        int r2=sc.nextInt(); 
        System.out.println("Rectangle sum "+ findsum3(matix, l1, r1, l2, r2));
    }
}
