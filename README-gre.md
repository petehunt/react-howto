# react-howto

Αν είσαι καινούριος στο React (ή στο frontend γενικότερα) μπορεί το οικοσύστημα να σου φαινεται δύσκολο. Υπάρχουν αρκετοί λόγοι που το προκαλούν αυτό.

* Το React ιστορικά στοχεύει αυτόυς που το χρησιμοποίησαν εξ αρχής και ανθρώπους με μεγάλη εμπειρία
* Το Facebook κάνει open-source ότι αυτό χρησιμοποιεί, οπότε δεν δίνει μεγάλη έμφαση στα εργαλεία που μπορούν να χρησιμοποιηθούν για μικρότερες από της Facebook εφαρμογές 
* Υπάρχουν πολλοί React οδηγοί κακής ποιότητας που λειτουργούν ως κακή διαφήμιση του React

Κατά τη διάρκεια αυτού του αρχείου, θα υποθέσω πως έχετε χτίσει μια εφαρμογή χρησιμοποιώντας HTML, CSS και Javascript.

## Γιατί θα πρέπει να ακούσετε εμένα;

Υπάρχουν χιλιάδες συμβουλές εκεί εξώ, γιατί να ακούσετε εμένα;

Ήμουν ένα από τα αρχικά μέλη της ομάδας του Facebook που έχτισαν και έκαναν open-source το React. Δεν δουλέυω πια στο Facebook και είμαι πλέον σε μια μικρή startup, οπότε έχω και τη μη-Facebook οπτική.

## Πως να ξεκινήσετε με το οικοσύστημα του React

Όλο το software είναι χτισμένο βασισμένο σε ένα σύνολο τεχνολογιών και πρέπει να καταλάβετε πως λειτουργούν αυτές για να μπορέσετε να χτίσετε τη δική σας εφαρμογή. Ο λόγος για τον οποίο το οικοσύστημα του React είναι τόσο πολύπλοκο είναι επειδή πάντα διδάσκεται με λάθος σειρά.

Θα πρέπει να τα μάθετε με αυτή τη σειρά **χωρίς να περάσετε κάποιο ή να μαθαίνετε πολλά ταυτόχρονα**:

* [React το ίδιο](#learning-react-itself)
* [`npm`](#learning-npm)
* [JavaScript “bundlers”](#learning-javascript-bundlers)
* [ES6](#learning-es6)
* [Routing](#learning-routing)
* [Flux](#learning-flux)

**Δεν είναι ανάγκη να τα μάθετε όλα αυτά για να είστε έτοιμοι να φτιάξετε κάτι έτοιμο για παραγωγή με React.** Περάστε σε επόμενο βήμα μόνο αν έχετε ένα πρόβλημα που πρέπει να λύσετε.

Επίσης υπάρχουν κάποιοι τομείς που αναφέρονται συχνά στην React κοινότητα και είναι στην "αιμορραγία άκρη". Οι παρακάτω τομείς είναι πολύ ενδιαφέροντες αλλά είναι δυσνόητοι, λιγότερο διαδεδομένοι από τους πάνω τομείς **και δεν χρειάζονται για τις περισσότερες εφαρμογές**.
* [Inline styles](#learning-inline-styles)
* [Server rendering](#learning-server-rendering)
* [Immutable.js](#learning-immutablejs)
* [Relay, Falcor, etc](#learning-relay-falcor-etc)

## Μαθαίνοντας το ίδιο το React

Είναι μια γνωστή παρανόηση πως πρέπει να ξοδέψετε πολύ χρόνο για να στήσετε τα εργαλεία για να ξεκινήσετε να μαθαίνετε React. Στα επίσημα έγγραφα θα βρείτε ένα [copy-paste HTML template](https://facebook.github.io/react/docs/getting-started.html#quick-start-without-npm) που μπορείτε να σώσετε σε ένα `.html` αρχείο και να ξεκινήσετε κατ' ευθείαν.  **Δεν χρειάζονται εργαλεία για αυτό το βήμα, και δεν θα χρειαστεί να μάθετε επιπλέον εργαλεία μέχρι να αισθάνεστε άνετα με τις βασικές ιδέες του React**

Ακόμα πιστεύω πως ο ευκολότερος τρόπος να μάθετε React είναι [ο επίσημος οδηγός](https://facebook.github.io/react/docs/tutorial.html).

## Μαθαίνοντας `npm`

`npm` είναι ο διαχειριστής πακέτων του Node.js και είναι ο πιο διαδεδομένος τρόπος οι frontend προγραμματιστές και οι σχεδιαστές μοιράζονται Javascript κώδικα. Περιλαμβάνει ένα σύστημα μονάδας που λέγεται `CommonJS` και σε αφήνει να εγκαταστήσεις εργαλεία γραμμής εντολών που είναι γραμμένα σε Javascript. Διαβάστε [αυτό το άρθρο](http://0fps.net/2013/01/22/commonjs-why-and-how/) για να δείτε γιατί το `CommonJS` είναι απαραίτητο για τα προγράμματα περιήγησης, ή το [CommonJS Spec Wiki](http://wiki.commonjs.org/wiki/Introduction) για περισσότερες πληροφορίες για το `CommonJS` API.

Τα περισσότερα επαναχρησιμοποιήμενα μέρη, βιβλιοθήκες και εργαλεία στο React οικοσύστημα μπορούν να βρεθούν ως `CommonJS` μέρη και εγκαταστώνται μέσω του `npm`.

## Μαθαίνοντας JavaScript bundlers

Για ένα σύνολο καλών τεχνικών λόγων τα `CommonJS` μέρη (π.χ. τα πάντα μέσα στο `npm`) δεν μπορούν να χρησιμοποιηθούν άμεσα στην ιστοσελίδα σας. Χρειάζεστε ένα JavaScript “bundler” για να κάνετε “bundle” αυτά τα μέρη σε `.js` αρχεία που μπορείτε να εισάγετε στην ιστοσελίδα σας με ενα `<script>` tag.

Παραδείγματα JavaScript bundlers περιλαμβάνουν το `webpack` και το `browserify`. Και τα δυο είναι καλές επιλογές, αλλά προτιμώ το `webpack` διότι παρέχει πολλές επιλογές που κάνουν τον προγραμματισμό για μεγάλες εφαρμογές πιο εύκολο. Αφού τα έγγραφά τους είναι λίγο δυσνόητα έχω ένα [plug-and-play template για να ξεκινήσετε](https://github.com/petehunt/react-webpack-template) και έχω γράψει ένα [how-to οδηγό για το webpack](https://github.com/petehunt/webpack-howto) για πιο δύσκολες περιπτώσεις.

Το React επίσης προσφέρει πλέον [ένα επίσημο CLI εργαλείο που λέγεται Create React App](https://github.com/facebookincubator/create-react-app). Σε αφήνει να δημιουργείς React εφαρμογές χρησιμοποιώντας το `webpack` χωρίς καμία παραμετροποιήση. Έχει τους περιορισμούς του, αλλά μπορεί να χρησιμοποιηθεί σαν πολύ καλή αρχή και οι αναβαθμίσεις του θα προσθέσουν περισσότερες επιλογές με τον καιρό. Προσφέρει επίσης μια "ejection" επιλογή που αντιγράφει όλες τις παραμετροποιήσεις στην εφαρμογή οπότε έχετε απόλυτο έλεγχο πάνω τους.

Ένα πράγμα που πρέπει να κρατάτε στο μυαλό σας είναι: `CommonJS` χρησιμοποιεί την `require()` λειτουργία για να εισάγει νέα μέρη, οπότε πολλοί νομίζουν πως έχει να κάνει με ένα project που λέγεται `require.js`. Για ένα σύνολο λόγων, θα πρότεινα να αποφεύγετε το `require.js`. Επίσης δεν είναι πολύ διαδεδομένο στο React οικοσύστημα.

## Μαθαίνοντας ES6

Εκτός απο το JSX (που μάθατε στο React tutorial), μπορεί να είδατε κάποιο περίεργο συντακτικό στα React παραδδείγματα. Αυτό λέγεται ES6 και είναι η τελευταία έκδοση της Javascript, οπότε μπορεί να μην το έχετε μάθει ακόμα. Αφού είναι τόσο καινούριο δεν υποστηρίζεται στα προγράμματα περιήγησης ακόμα, αλλά το bundler σας μπορεί να το μεταφράσει για σας με την κατάλληλη παραμετροποίηση.

Αν θέλετε απλά να κάνετε πράγματα με το React **μπορείτε να προσπεράσετε την εκμάθηση του ES6**, ή να προσπαθήσετε να το μάθετε στην πορεία.

Μπορεί να δείτε κάποιες συζητήσεις για ES6 κλάσεις να είναι ο αγαπημένος τρόπος για να δημιουργείτε τα React components. Αυτό δεν είναι αλήθεια. Οι περισσότεροι άνθρωποι (συμπεριλαμβάνοντας το Facebook) χρησιμοποιούν το `React.createClass()`.

## Μαθαίνοντας το routing

Τα “single-page applications” είναι πολυσυζητημένα αυτές τις μέρες. Αυτά είναι σελίδες που φορτώνουν μια φορά και όταν ο χρήστης πατάει σε ένα link ή ένα κουμπί, το Javascript που τρέχει στη σελίδα ανανεώνει το address bar, αλλά η σελίδα δεν ξαναφορτώνει. Η διαχείριση του address bar γίνεται με κάτι που λέγεται **router**.

Το πιο διαδεδομένο router στο React οικοσύστημα είναι το [react-router](https://github.com/rackt/react-router). Αν χτίζετε ένα single-page application, χρησιμοποιήστε το εκτός αν έχετε κάποιο καλό λόγο να μην το κάνετε.

**Μην χρησιμοποιείτε router αν δεν χτίζετε ένα single-page application**. Τα περισσότερα projects ξεκινάνε ως μικρότερα μέρη μέσα σε μια μεγαλύτερη εφαρμογή έτσι κι αλλιώς.

## Μαθαίνοντας Flux

Λογικά έχετε ακούσει το Flux. Υπάρχουν *άπειρη* παραπληροφόρηση για το Flux εκεί έξω.

Πολλοί άνθρωποι κάθονται να χτίσουν μια εφαρμογή και θέλουν να διευκρινίσουν το data model τους και νομίζουν πως πρέπει να χρησιμοποίησουν το Flux για να το κάνουν. **Αυτός έιναι ο λάθος τρόπος σκέψης για να χρησιμοποιηθεί το Flux. Το Flux πρέπει να προστεθεί μόνο όταν πολλά componnets έχουν χτιστεί.**

Τα React components είναι φτιαγμένα με μια ιεραρχία. Τις περισσότερες φορές το data model επίσης ακολουθεί αυτή την ιεραρχία. Σε αυτές τις περιπτώσεις το Flux δεν χρησιμεύει και πολύ. Μερικές φορές βέβαια, το data model δεν ακολουθεί την ιεραρχία αυτή. Όταν τα React components ξεκινήσουν να λαμβάνουν `props` που δεν νοιώθετε πως είναι στο σωστό μέρος, ή έχετε ε΄να μικρό αριθμό components που ξεκινάνε να γίνονται πολύπλοκα, τότε μπορεί να θελήσετε να κοιτάξετε το Flux.

**Θα καταλάβετε όταν θα χρειαστείτε το Flux. Αν δεν είστε σίγουροι ότι το χρειάζεστε, τότε δεν το χρειάζεστε.**

Αν αποφασίσατε πως θα το χρησιμοποιήσετε η πιο γνωστή και καλογραμμένη βιβλιοθήκη είναι το [Redux](http://redux.js.org/). Υπάρχουν *άπειρες* εναλλακτεικές εκεί έξω και θα θελήσετε να δοκιμάσετε πολλές από αυτές, αλλά η συμβουλή μου είναι να μείνετε με την πιο διαδεδομένη.

## Μαθαίνοντας inline styles

Pre-React, a lot of people reused CSS styles with complicated style sheets built by preprocessors like SASS. Since React makes writing reusable components easy, your stylesheets can be less complicated. Many in the community (including myself) are experimenting with getting rid of stylesheets altogether.

This is a fairly crazy idea for a number of reasons. It makes media queries more difficult, and it's possible that there are  performance limitations using this technique. **When starting out with React, just style things the way you normally would.**

Once you've got a feel for how React works, you can look at alternate techniques. One popular one is [BEM](https://en.bem.info/). I recommend phasing out your CSS preprocessor, since React gives you a more powerful way to reuse styles (by reusing components) and your JavaScript bundler can generate more efficient stylesheets for you (I gave [a talk about this at OSCON](https://www.youtube.com/watch?v=VkTCL6Nqm6Y)). With that said, React, like any other JavaScript library, will work just fine with a CSS preprocessor.

Alternatively, you can also use [CSS Modules](http://glenmaddern.com/articles/css-modules), more specifically [react-css-modules](https://github.com/gajus/react-css-modules). With CSS Modules you'll still write CSS (or SASS/LESS/Stylus), but you can manage and compose your CSS files like you'd do with inline styles in React. And you don't need to worry about managing your class names using methodologies like BEM, as this will be handled for you under the hood by the module system.

## Learning server rendering

Server rendering is often called "universal" or "isomorphic" JS. It means that you can take your React components and render them to static HTML on the server. This improves initial startup performance because the user does not need to wait for JS to download in order to see the initial UI, and React can re-use the server-rendered HTML so it doesn't need to generate it client-side.

You need server rendering if you notice that your initial render is too slow or if you want to improve your search engine ranking. While it's true that Google now indexes client-rendered content, as of January 2016 every time it's been measured it's been shown to negatively affect ranking, potentially because of the performance penalty of client-side rendering.

Server rendering still requires a lot of tooling to get right. Since it transparently supports React components written without server rendering in mind, you should build your app first and worry about server rendering later. You won't need to rewrite all of your components to support it.

## Learning Immutable.js

[Immutable.js](https://facebook.github.io/immutable-js/) provides a set of data structures that can help to solve certain performance issues when building React apps. It's a great library, and you'll probably use it a lot in your apps moving forward, but it's completely unnecessary until you have an appreciation of the performance implications. 

## Learning Relay, Falcor etc

These are technologies that help you reduce the number of AJAX requests. They’re still very cutting-edge, so if you don’t have a problem with too many AJAX requests, you don’t need Relay or Falcor.
