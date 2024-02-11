# Lab Report 3 <br/>
In this week's lab, we debugged and used more commands!

## Part 1 <br/>
## A failure-inducing input for the buggy program, as a JUnit test and any associated code.
```
@Test 
	public void testReverseInPlace() {
    int[] input2 ={1, 2};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{2, 1}, input2);
	}
```
The test expected `{2, 1}` as the output but instead got `{2, 1}`. 

## An input that doesn't induce a failure, as a JUnit test and any associated code

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
```
## The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
![Image](ss1forlabreport3.png)
## The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
Before: 
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
}
```
After:
```
static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for (int i = 0; i < newArray.length; i++){
      arr[i] = newArray[i];
    }
}
```
Before, there was only one array which posed a problem. For instance, when we are trying to update the last element to the original first element, the original first element has already been updated to the last element. In the fixed code, there is a new array where we can leave the input array as is when reversing it. Then we copy all the elements from the new array to the input array to get the desired result. 

## Part 2
## grep -r 
```
miachen@Mias-MacBook-Air-6 lab5 % grep -r "World War II" technical/
technical//government/Gen_Account_Office/Testimony_cg00010t.txt:With the U.S. entry into World War II, GAO faced enormous
technical//government/Gen_Account_Office/d03232sp.txt:Since World War II, the Congress has clarified and expanded that
technical//government/Gen_Account_Office/d01591sp.txt:20Since World War II, annual growth in GDP per capita has
technical//government/Gen_Account_Office/d01591sp.txt:every 35 years. Since World War II, annual growth in GDP per capita
technical//government/Media/It_Pays_to_Know.txt:Lee Kemp, a hearing-impaired World War II disabled vet, also was
technical//plos/journal.pbio.0020101.txt:        coincidentally after World War II, was Konrad Lorenz (1966). Lorenz's thesis was greeted
technical//plos/journal.pbio.0020067.txt:        defense—the cavity magnetron that may have turned the course of World War II.
technical//plos/journal.pbio.0020067.txt:        Bernal, and Dorothy Hodgkin. The other was the pre-World War II work of William Astbury in
technical//biomed/bcr583.txt:        Norwegian women who were adolescents during World War II,
technical//911report/chapter-13.5.txt:                World War II (Oxford Univ. Press, 1988), p. 215.
technical//911report/chapter-13.1.txt:            The men and women of the World War II generation rose to the challenges of the 1940s
technical//911report/chapter-3.txt:            The FBI's domestic intelligence gathering dates from the 1930s. With World War II
technical//911report/chapter-3.txt:                in World War II after having first thought the FBI might take that role. The father
technical//911report/chapter-3.txt:            At the end of World War II, to Donovan's disappointment, President Harry Truman
technical//911report/chapter-3.txt:                following World War II. The Congressional Reorganization Act of 1946 created the
technical//911report/chapter-2.txt:                progress. After gaining independence from Western powers following World War II, the
```
`grep -r` can be useful for searching for certain words in files under a certain directory. Without `-r`, `grep "World War II" technical/` would fail, saying that `technical/` is a directory, not a file. 
## grep -r
```
miachen@Mias-MacBook-Air-6 lab5 % grep -r ".txt" technical/
technical//biomed/gb-2003-4-5-r34.txt:            20,000), and repeat the process. The Readme.txt file
technical//biomed/gb-2001-2-7-research0025.txt:        Pfam_Annotation.txt
technical//biomed/gb-2001-2-7-research0025.txt:        Protein_Annotation.txt
technical//biomed/gb-2002-3-7-research0037.txt:        README.txt contains instructions for installation and
technical//biomed/gb-2002-3-6-software0001.txt:        as .txt files (tab-delimited text, refer to the user's
technical//biomed/gb-2002-3-12-research0078.txt:          .txt extension.
technical//biomed/gb-2001-2-9-research0037.txt:          hyb2dis.txt in additional data files). More importantly,
technical//biomed/gb-2001-2-9-research0037.txt:        hyb2dis.txt: patch file that converts White's hybridize
technical//biomed/gb-2001-2-9-research0037.txt:        Training sets(GlycineMedicago.txt,Rhizobia.txt,
technical//biomed/gb-2001-2-9-research0037.txt:        Stramenopiles.txt, ZygoChytrid.txt): FASTA-formatted text
technical//biomed/gb-2001-2-9-research0037.txt:        Test sets(PsojaeHA.txt, PsojaeMY.txt, PsojaeZO.txt,
technical//biomed/gb-2001-2-9-research0037.txt:        MtRHE.txt, DSIR.txt, MHAM.txt, KV0.txt, KV2.txt, KV3.txt):
technical//biomed/gb-2001-2-9-research0037.txt:        hyb2dis.txt
technical//biomed/gb-2001-2-9-research0037.txt:        hyb2dis.txt
technical//biomed/gb-2001-2-9-research0037.txt:        GlycineMedicago.txt
technical//biomed/gb-2001-2-9-research0037.txt:        Rhizobia.txt
technical//biomed/gb-2001-2-9-research0037.txt:        Stramenopiles.txt
technical//biomed/gb-2001-2-9-research0037.txt:        ZygoChytrid.txt
technical//biomed/gb-2001-2-9-research0037.txt:        PsojaeHA.txt
technical//biomed/gb-2001-2-9-research0037.txt:        PsojaeMY.txt
technical//biomed/gb-2001-2-9-research0037.txt:        PsojaeZO.txt
technical//biomed/gb-2001-2-9-research0037.txt:        MtRHE.txt
technical//biomed/gb-2001-2-9-research0037.txt:        DSIR.txt
technical//biomed/gb-2001-2-9-research0037.txt:        KV0.txt
technical//biomed/gb-2001-2-9-research0037.txt:        KV2.txt
technical//biomed/gb-2001-2-9-research0037.txt:        KV3.txt
technical//biomed/1471-2105-2-9.txt:            of files (e.g., seq or txt files) or from a
technical//biomed/1471-2105-2-9.txt:            fasta_groups.txt output file contains the group name
technical//biomed/1471-2105-2-9.txt:            format. The fasta_groups.txt file is particularly
technical//biomed/1471-2105-2-9.txt:            output file, group_seqs.txt, contains the group name
technical//biomed/1471-2105-2-9.txt:            output file, group_files.txt, contains the group name,
technical//biomed/1471-2105-2-9.txt:            file, coverage.txt, shows how many sequences are in
technical//biomed/1471-2105-2-9.txt:            Good [ 7 ] . Finally, the infile.txt file contains all
technical//biomed/1471-2105-2-9.txt:          from the 3' end and looking at the group_seqs.txt output
technical//biomed/1471-2105-2-9.txt:          to the fasta_groups.txt file, which is ideal for Clustal
technical//biomed/gb-2002-3-12-research0071.txt:        'EtOH.txt', 'SwiSnfMin.txt'and 'SwiSnfRich.txt', and
technical//biomed/gb-2002-3-12-research0071.txt:        'Zinc.txt'.
technical//biomed/1471-2105-2-1.txt:          Also attached are a users' manual (user.txt - see
technical//biomed/1471-2105-3-6.txt:          readme.txt documentation file are also included.
technical//biomed/1471-2105-3-4.txt:          conversions of .chp (.txt) for each individual profile
```
This is interesting to see: `grep` only searches for the contents of a file, not the file names/extensions of files. It is not as useful when examining file names.
## grep -r --exclude-dir
```miachen@Mias-MacBook-Air-6 lab5 % grep -r --exclude-dir="911report" "World War II" technical/
technical//government/Gen_Account_Office/Testimony_cg00010t.txt:With the U.S. entry into World War II, GAO faced enormous
technical//government/Gen_Account_Office/d03232sp.txt:Since World War II, the Congress has clarified and expanded that
technical//government/Gen_Account_Office/d01591sp.txt:20Since World War II, annual growth in GDP per capita has
technical//government/Gen_Account_Office/d01591sp.txt:every 35 years. Since World War II, annual growth in GDP per capita
technical//government/Media/It_Pays_to_Know.txt:Lee Kemp, a hearing-impaired World War II disabled vet, also was
technical//plos/journal.pbio.0020101.txt:        coincidentally after World War II, was Konrad Lorenz (1966). Lorenz's thesis was greeted
technical//plos/journal.pbio.0020067.txt:        defense—the cavity magnetron that may have turned the course of World War II.
technical//plos/journal.pbio.0020067.txt:        Bernal, and Dorothy Hodgkin. The other was the pre-World War II work of William Astbury in
technical//biomed/bcr583.txt:        Norwegian women who were adolescents during World War II,
```
## grep -r 
```
miachen@Mias-MacBook-Air-6 lab5 % grep -r --exclude-dir="911report" --exclude-dir="government" "World War II" technical/
technical//plos/journal.pbio.0020101.txt:        coincidentally after World War II, was Konrad Lorenz (1966). Lorenz's thesis was greeted
technical//plos/journal.pbio.0020067.txt:        defense—the cavity magnetron that may have turned the course of World War II.
technical//plos/journal.pbio.0020067.txt:        Bernal, and Dorothy Hodgkin. The other was the pre-World War II work of William Astbury in
technical//biomed/bcr583.txt:        Norwegian women who were adolescents during World War II
```

